---
title: Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: 539ac998a557615c097c33cdd4207e99f396e81d
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959617"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme
Yönetilen HTML belgesi nesne modeli (DOM) adlı bir sınıf içerir <xref:System.Windows.Forms.HtmlElement> özellikleri, yöntemleri ve tüm HTML öğeleri ortak olan olayları gösterir. Bazı durumlarda, ancak yönetilen arabirimi doğrudan kullanıma üyelere erişim ihtiyacınız olacak. Bu konuda, bir Web sayfası tanımlanmış JScript ve VBScript işlevleri dahil olmak üzere gösterilmeyen üyelere erişim için iki şekilde inceler.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Yönetilen arabirimleri aracılığıyla gösterilmeyen öğelere erişme  
 <xref:System.Windows.Forms.HtmlDocument> ve <xref:System.Windows.Forms.HtmlElement> gösterilmeyen erişiminizi etkinleştirecek olan dört yöntemleri sağlar. Aşağıdaki tabloda, türleri ve bunların karşılık gelen yöntemleri gösterilmektedir.  
  
|Üye Türü|Yöntemleri|  
|-----------------|-----------------|  
|Özellikler (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Yöntemler|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Olaylar (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Olaylar (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Olaylar (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Bu yöntemi kullandığınızda, temel alınan doğru türünde bir öğe sahip olduğunuz varsayılır. Dinlenecek istediğinizi varsayın `Submit` olayı bir `FORM` öğe üzerinde bir HTML sayfası, böylece bazı ön işleme gerçekleştirebileceğiniz `FORM`ait kullanıcı bunları server için göndermeden önce değerleri. İdeal olarak, HTML denetime varsa tanımlayın `FORM` benzersiz olmasını `ID` özniteliği.  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 Bu sayfaya yükledikten sonra <xref:System.Windows.Forms.WebBrowser> kullanabileceğiniz denetimi <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> alınacak yöntemi `FORM` kullanarak çalışma zaman `form1` bağımsız değişken olarak.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Yönetilmeyen arabirimler erişme  
 Yönetilen HTML DOM gösterilmeyen her DOM sınıfı tarafından kullanıma sunulan yönetilmeyen Bileşen Nesne Modeli (COM) arabirimlerini kullanarak da erişebilirsiniz. Gösterilmeyen üyelere karşı çeşitli çağrılar yapmak varsa veya gösterilmeyen yönetilen HTML DOM tarafından Sarmalanan değil diğer yönetilmeyen arabirimler döndürürse bu önerilir  
  
 Aşağıdaki tabloda tüm yönetilen HTML DOM kullanıma sunulan yönetilmeyen arabirimler gösterir Kullanım ve örnek kod açıklaması için her bağlantısına tıklayın.  
  
|Tür|Yönetilmeyen arabirimi|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 Bu desteklenmeyen olmasına rağmen COM arabirimleri kullanması için en kolay yolu (MSHTML.dll) yönetilmeyen HTML DOM kitaplığına bir başvuru, uygulamanızdan eklemektir. Daha fazla bilgi için [Bilgi Bankası makalesi 934368](https://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>Betik işlevleri erişme  
 Bir HTML sayfası, bir veya daha fazla işlev JScript veya VBScript gibi bir betik dilini kullanarak tanımlayabilirsiniz. Bu işlevlerin içine yerleştirilen bir `SCRIPT` sayfasında sayfasında ve isteğe bağlı veya bir olaya yanıt olarak yerli üzerinde çalıştırılabilir  
  
 Tanımladığınız bir HTML sayfasını kullanarak içinde herhangi bir betik işlevleri çağırabilir <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> yöntemi. Komut dosyası yöntemi HTML öğesi döndürürse, bu dönüş sonuç dönüştürmek için bir yayın kullanabilirsiniz bir <xref:System.Windows.Forms.HtmlElement>. Ayrıntıları ve örnek kod için bkz: <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen HTML Belgesi Nesne Modelini Kullanma](using-the-managed-html-document-object-model.md)
