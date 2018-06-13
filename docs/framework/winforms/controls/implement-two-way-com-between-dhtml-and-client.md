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
ms.openlocfilehash: 90f4f4500514e2e3d7a231861c0cf4b3d453a4c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540624"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Nasıl yapılır: DHTML Koduyla İstemci Uygulaması Kodu Arasında İki Yönlü İletişim Gerçekleştirme
Kullanabileceğiniz <xref:System.Windows.Forms.WebBrowser> denetim Windows Forms istemci uygulamalarınızı varolan dinamik HTML (DHTML) Web uygulama kodu ekleyin. DHTML tabanlı denetimler oluşturma önemli geliştirme zamanı yatırım yaptıysanız ve var olan kodu yeniden yazmaya gerek kalmadan Windows Forms zengin bir kullanıcı arabirimi özelliklerini yararlanmak istediğinizde kullanışlıdır.  
  
 <xref:System.Windows.Forms.WebBrowser> Denetimi yapmanıza izin verir, istemci uygulaması kodu Web sayfası komut dosyası kodu aracılığıyla arasında iki yönlü iletişim uygulamanıza <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> ve <xref:System.Windows.Forms.WebBrowser.Document%2A> özellikleri. Ayrıca, yapılandırabileceğiniz <xref:System.Windows.Forms.WebBrowser> böylece Web denetimleri DHTML uygulamalarının gizleme uygulama formunuzda diğer denetimleri ile sorunsuz bir şekilde blend denetim. Arka plan rengi ve görsel stil formun kalanını eşleşmesi kullanın, görüntülenen sayfa sorunsuz bir şekilde denetimleri blend biçiminde <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, ve <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> standart tarayıcı özellikleri devre dışı bırakmak için özellikler.  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Windows Forms uygulaması'nda DHTML eklemek için  
  
1.  Ayarlama <xref:System.Windows.Forms.WebBrowser> denetimin <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> özelliğine `false` önlemek için <xref:System.Windows.Forms.WebBrowser> sürüklediğinizde bırakılan dosyaları açmasını denetim.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  Denetimin ayarlamak <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> özelliğine `false` önlemek için <xref:System.Windows.Forms.WebBrowser> kullanıcı tıklattığında Denetimi'nin kısayol menüsünü görüntüleme.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  Denetimin ayarlamak <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> özelliğine `false` önlemek için <xref:System.Windows.Forms.WebBrowser> kısayol tuşları yanıt denetimi.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  Ayarlama <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> formun Oluşturucusu özelliğinde veya <xref:System.Windows.Forms.Form.Load> olay işleyicisi.  
  
     Aşağıdaki kod komut dosyası nesnesi için form sınıfı kullanır.  
  
    > [!NOTE]
    >  Bileşen Nesne Modeli (COM) komut dosyası nesnesi erişebilmeleri gerekir. Formunuz COM görünür yapmak için add <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliği form sınıfı.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  Ortak özellikler ve yöntemler uygulama kodunuzda betik kodunuzu kullanacağı uygulayın.  
  
     Örneğin, komut dosyası nesne için form sınıfı kullanırsanız, form sınıfa aşağıdaki kodu ekleyin.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  Kullanım `window.external` genel özellikleri ve yöntemleri belirtilen nesnenin erişmek için komut dosyası kodunuzda nesnesi.  
  
     Aşağıdaki HTML kodu bir düğmesini tıklatın komut dosyası nesnesinde bir yöntem çağrısı gösterilmiştir. Bu kodu bir HTML belgesinin denetimin kullanarak yük gövde öğesinin içine kopyalayın <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemi veya denetimin atamak <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özelliği.  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  İşlevler betik kodunuzu, uygulama kodunuzda kullanacağınız uygulayın.  
  
     Aşağıdaki HTML komut dosyası öğesi, bir örnek işlevi sağlar. Bu kodu denetimin kullanarak yük bir HTML belgesinin HEAD öğesinin içine kopyalayın <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemi veya denetimin atamak <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özelliği.  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  Kullanım <xref:System.Windows.Forms.WebBrowser.Document%2A> kod istemci uygulama kodunuzdan erişmek için özellik.  
  
     Örneğin, bir düğmeye aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisi.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. Hata ayıklama, DHTML işiniz bittiğinde, denetimin ayarlamak <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> özelliğine `true` önlemek için <xref:System.Windows.Forms.WebBrowser> komut dosyası kodu sorunları için hata iletileri görüntüleme denetimi.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki tam kod örneği, bu özellik anlamak için kullanabileceğiniz bir tanıtım uygulaması sağlar. HTML kod yüklenen <xref:System.Windows.Forms.WebBrowser> aracılığıyla kontrol <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> ayrı bir HTML dosyasından yüklenen yerine özelliği.  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu gerektirir:  
  
-   Sistem ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [WebBrowser Denetimi](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
