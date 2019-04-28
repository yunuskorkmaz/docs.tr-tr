---
title: 'Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde Bir Öğedeki Stilleri Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 804041991199dd2722e3a0f38800bafd8933bbab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608404"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde Bir Öğedeki Stilleri Değiştirme

Bir belge ve onun öğelerine görünümünü kontrol etmek için HTML stillerini kullanabilirsiniz. <xref:System.Windows.Forms.HtmlDocument> ve <xref:System.Windows.Forms.HtmlElement> Destek <xref:System.Windows.Forms.HtmlElement.Style%2A> stili dizeler aşağıdaki biçimde ele özellikleri:

`name1:value1;...;nameN:valueN;`

İşte bir `DIV` bir stil dizesiyle kalın Arial ve tüm metin yazı tipini ayarlar:

`<DIV style="font-face:arial;font-weight:bold;">`

`Hello, world!`

`</DIV>`

Düzenleme stilleri kullanarak sorunu <xref:System.Windows.Forms.HtmlElement.Style%2A> özelliği ekleyin ve dizesi bağımsız stil ayarları kaldırmak için hantal kanıtlayabilirsiniz. Örneğin, karmaşık bir yordam, önceki metni italik kullanıcı imleci üzerine konumlandırır. her işleme olacak `DIV`ve imleci ayrıldığında kapalı italik yap `DIV`. Çok sayıda stilleri bu şekilde işlemek istiyorsanız zaman bir sorun oluşur.

Aşağıdaki yordam, HTML belgeleri ve öğeleri stilleri kolayca yönetmek için kullanabileceğiniz kodu içerir. Yordamı, yeni proje oluşturma ve bir forma denetim ekleme gibi Windows Forms'da temel görevleri gerçekleştirme bilmeniz gerekir.

### <a name="to-process-style-changes-in-a-windows-forms-application"></a>Bir Windows Forms uygulamasında stil değişikliklerini işlemek için

1. Yeni bir Windows Forms projesi oluşturun.

2. Programlama diliniz için uygun uzantısında bitiş yeni bir sınıf dosyası oluşturun.

3. Kopyalama `StyleGenerator` sınıfı dosyasına kod bu konunun Örnek bölümünde sınıfı ve kodu kaydedin.

4. Aşağıdaki HTML'yi Test.htm adlı bir dosyaya kaydedin.

    ```html
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

5. Ekleme bir <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1` projenizin ana formu için.

6. Projenizin kod dosyasına aşağıdaki kodu ekleyin.

    > [!IMPORTANT]
    >  Emin `webBrowser1_DocumentCompleted` olay işleyicisi için bir dinleyici olarak yapılandırıldığında <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olay. Visual Studio'da çift tıklayarak <xref:System.Windows.Forms.WebBrowser> denetimi; bir metin düzenleyicisinde dinleyiciyi programlı bir şekilde yapılandırın.  
  
     [!code-csharp[ManagedDOMStyles#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7. Projeyi çalıştırın. İmlecinizi ilk çalıştırma `DIV` kod etkilerini gözlemleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için tam kod gösterilir `StyleGenerator` varolan bir stili değeri ayrıştırır, sınıf, destekler ekleme, değiştirme ve kaldırma stiller ve istenen değişiklikler yeni bir stil değeriyle döndürür.  
  
 [!code-csharp[ManagedDOMStyles#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.HtmlElement>
