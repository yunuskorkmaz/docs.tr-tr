---
title: 'Nasıl yapılır: DHTML Koduyla İstemci Uygulaması Kodu Arasında İki Yönlü İletişim Gerçekleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
ms.openlocfilehash: 26cbc995a749c4c129729be700dee588d1033a05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953431"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Nasıl yapılır: DHTML Koduyla İstemci Uygulaması Kodu Arasında İki Yönlü İletişim Gerçekleştirme

Bu denetimi, <xref:System.Windows.Forms.WebBrowser> Windows Forms istemci uygulamalarınıza var olan dinamik HTML (DHTML) Web uygulaması kodu eklemek için kullanabilirsiniz. Bu, DHTML tabanlı denetimler oluşturma konusunda önemli bir geliştirme süresi yatırdığınızda ve mevcut kodu yeniden yazmak zorunda kalmadan Windows Forms zengin Kullanıcı arabirimi özellikleri avantajlarından yararlanmak istediğinizde yararlıdır.

Denetim, <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> ve<xref:System.Windows.Forms.WebBrowser.Document%2A> özellikleri aracılığıyla istemci uygulama kodunuz ile Web sayfanızın betik oluşturma kodu arasında iki yönlü iletişim uygulamanıza olanak sağlar. <xref:System.Windows.Forms.WebBrowser> Ayrıca, <xref:System.Windows.Forms.WebBrowser> denetimi, Web denetimlerinizin uygulama formunuzdaki diğer denetimlerle sorunsuz bir şekilde karışmasını sağlayacak şekilde, DHTML uygulamasını gizleyerek yapılandırabilirsiniz. Denetimleri sorunsuzca karıştırmak için, sayfanın arka plan rengi ve görsel stilinin formun geri kalanıyla eşleşmesi için görüntülenen sayfayı biçimlendirin ve standart tarayıcı özelliklerini devre dışı bırakmak için <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>ve <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> özelliklerini kullanın.

## <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Windows Forms uygulamanıza DHTML eklemek için

1. Denetimin üzerinde bırakılan dosyaları <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> açmasını engellemek `false` için denetiminözelliğiniolarakayarlayın.<xref:System.Windows.Forms.WebBrowser> <xref:System.Windows.Forms.WebBrowser>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]

2. Kullanıcı sağ tıkladığında <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> <xref:System.Windows.Forms.WebBrowser> denetimin kısayol menüsünü `false` görüntülemesini engellemek için denetimin özelliğini olarak ayarlayın.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]

3. Denetimin kısayol tuşlarına yanıt <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vermesini engellemek `false` için denetimin özelliğini olarak ayarlayın. <xref:System.Windows.Forms.WebBrowser>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]

4. Formun oluşturucusunda veya bir <xref:System.Windows.Forms.Form.Load> olay işleyicisinde özelliğiayarlayın.<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>

     Aşağıdaki kod, komut dosyası nesnesi için form sınıfının kendisini kullanır.

    > [!NOTE]
    > Bileşen nesne modeli (COM), betik nesnesine erişebilmelidir. Formunuzu com 'a görünür hale getirmek için <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliğini form sınıfınıza ekleyin.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]

5. Betik kodunuzun kullanacağı uygulama kodunuzda ortak özellikleri veya yöntemleri uygulayın.

     Örneğin, betik nesnesi için form sınıfını kullanırsanız, form Sınıfınıza aşağıdaki kodu ekleyin.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]

6. Belirtilen nesnenin ortak özelliklerine ve yöntemlerine erişmek için komut dosyası kodunuzda nesnesinikullanın.`window.external`

     Aşağıdaki HTML kodu, bir düğme tıklaağından betik nesnesi üzerinde bir yöntemin nasıl çağrılacağını gösterir. Bu kodu, denetimin <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemini kullanarak yüklediğiniz veya <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> denetimin özelliğine atadığınız bir HTML belgesinin Body öğesine kopyalayın.

    ```html
    <button onclick="window.external.Test('called from script code')">
        call client code from script code
    </button>
    ```

7. Betik kodunuzda, uygulama kodunuzun kullanacağı işlevleri uygulayın.

     Aşağıdaki HTML BETIĞI öğesi örnek bir işlev sağlar. Bu kodu, denetimin <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemini kullanarak yüklediğiniz veya <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> denetimin özelliğine atadığınız bir HTML belgesinin baş öğesine kopyalayın.

    ```html
    <script>
    function test(message) {
        alert(message);
    }
    </script>
    ```

8. İstemci uygulama kodunuzda betik koduna erişmek için özelliğinikullanın.<xref:System.Windows.Forms.WebBrowser.Document%2A>

     Örneğin, bir düğme <xref:System.Windows.Forms.Control.Click> olay işleyicisine aşağıdaki kodu ekleyin.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]

9. DHTML kodunuzda hata ayıklamayı tamamladıktan sonra, <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> <xref:System.Windows.Forms.WebBrowser> denetimin komut dosyası kodu sorunları için hata `true` iletilerini görüntülemesini engellemek için denetimin özelliğini olarak ayarlayın.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bu özelliği anlamak için kullanabileceğiniz bir tanıtım uygulaması sağlar. HTML kodu, ayrı bir HTML dosyasından <xref:System.Windows.Forms.WebBrowser> yüklenmesi yerine <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özelliği aracılığıyla denetime yüklenir.

[!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]

## <a name="compiling-the-code"></a>Kod Derleniyor

Bu kod şunları gerektirir:

- System ve System. Windows. Forms derlemelerine başvurular.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [WebBrowser Denetimi](webbrowser-control-windows-forms.md)
