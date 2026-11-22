
import java.util.Scanner;

public class Main2 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        int boyAns = 0, girlAns = 0;

        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);

            // 处理 boy 的连续片段
            if (c == 'b' || c == 'o' || c == 'y') {
                int b = 0, o = 0, y = 0;
                while (i < s.length() && (s.charAt(i) == 'b' || s.charAt(i) == 'o' || s.charAt(i) == 'y')) {
                    char cur = s.charAt(i);
                    if (cur == 'b') b++;
                    else if (cur == 'o') o++;
                    else y++;
                    i++;
                }
                i--; // 回退一步，因为外层 for 循环还会 i++
                boyAns += Math.max(b, Math.max(o, y)); // 该片段需要的 boy 数量
            }

            // 处理 girl 的连续片段
            else if (c == 'g' || c == 'i' || c == 'r' || c == 'l') {
                int g = 0, iCnt = 0, r = 0, l = 0;
                while (i < s.length() && (s.charAt(i) == 'g' || s.charAt(i) == 'i' || s.charAt(i) == 'r' || s.charAt(i) == 'l')) {
                    char cur = s.charAt(i);
                    if (cur == 'g') g++;
                    else if (cur == 'i') iCnt++;
                    else if (cur == 'r') r++;
                    else l++;
                    i++;
                }
                i--;
                girlAns += Math.max(Math.max(g, iCnt), Math.max(r, l)); // 该片段需要的 girl 数量
            }
        }

        System.out.println(boyAns);
        System.out.println(girlAns);
    }
}
