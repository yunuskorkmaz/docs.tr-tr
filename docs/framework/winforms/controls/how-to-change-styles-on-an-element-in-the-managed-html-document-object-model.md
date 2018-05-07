---
title: 'Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde Bir Öğedeki Stilleri Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 9ecb6b90508ca53e3801a633ac2444426e2f8113
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde Bir Öğedeki Stilleri Değiştirme
Bir belge ve öğeleri görünümünü denetlemek için HTML stilleri kullanın. <xref:System.Windows.Forms.HtmlDocument> ve <xref:System.Windows.Forms.HtmlElement> Destek <xref:System.Windows.Forms.HtmlElement.Style%2A> stili dizeleri aşağıdaki biçimde ele özellikleri:  
  
 `name1:value1;...;nameN:valueN;`  
  
 Burada bir `DIV` bir stil dizesiyle kalın Arial ve tüm metnin yazı tipini ayarlar:  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 Düzenleme stilleri kullanarak sorun <xref:System.Windows.Forms.HtmlElement.Style%2A> özelliktir ekleyin ve tek tek stil ayarlarını dizeden kaldırmak için sıkıcı kanıtlayabilirsiniz. Örneğin, karmaşık bir yordam, önceki metni italik üzerinden imleci kullanıcı konumlandırır her işlemek olacak `DIV`ve imleci ayrıldığında kapalı italik yapın `DIV`. Çok sayıda stilleri bu şekilde işlemek gerekiyorsa zaman bir sorun oluşur.  
  
 Aşağıdaki yordam kolayca HTML belgeleri ve öğeleri stilleri düzenlemek için kullanabileceğiniz kodu içerir. Yordam için Windows Forms'ta yeni proje oluşturma ve bir forma denetim ekleme gibi temel görevleri gerçekleştirme bilmeniz gerekir.  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a>Stil işlemek için bir Windows Forms uygulamasında değiştirir.  
  
1.  Yeni bir Windows Forms projesi oluşturun.  
  
2.  Programlama diliniz için uygun uzantısında bitiş yeni bir sınıf dosyası oluşturun.  
  
3.  Kopya `StyleGenerator` sınıfı dosyasına kodunu örnek bölümünde bu konu, sınıf ve kod kaydedin.  
  
4.  Aşağıdaki HTML Test.htm adlı bir dosyaya kaydedin.  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  Ekleme bir <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1` projenizin ana formuna.  
  
6.  Projenizin kod dosyasına aşağıdaki kodu ekleyin.  
  
    > [!IMPORTANT]
    >  Emin `webBrowser1_DocumentCompleted` olay işleyicisi için bir dinleyici olarak yapılandırılmış <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olay. Visual Studio'da çift <xref:System.Windows.Forms.WebBrowser> denetlemek; bir metin düzenleyicisinde dinleyicisini programlı olarak yapılandırın.  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  Projeyi çalıştırın. İmleç ilk çalıştırma `DIV` kodun etkilerini izlemek için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için tam kodu gösterir `StyleGenerator` var olan bir stil değeri ayrıştırır, sınıf destekler ekleme, değiştirme ve kaldırma stilleri ve istenen değişiklikleri ile yeni bir stil değeri döndürür.  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.HtmlElement>
