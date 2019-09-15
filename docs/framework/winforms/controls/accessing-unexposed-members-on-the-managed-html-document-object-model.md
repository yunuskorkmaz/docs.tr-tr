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
ms.openlocfilehash: 525ef52ecbbc61fba787fa8286c56c638d837faf
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988396"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme
Yönetilen HTML belge nesne modeli (DOM), tüm HTML öğelerinin ortak <xref:System.Windows.Forms.HtmlElement> olan özelliklerini, yöntemlerini ve olaylarını sunan adlı bir sınıf içerir. Ancak bazen, yönetilen arabirimin doğrudan sergilemediği üyelere erişmeniz gerekir. Bu konu, bir Web sayfası içinde tanımlanan JScript ve VBScript işlevleri de dahil olmak üzere, gösterilmeyen üyelere erişmenin iki yolunu inceler.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Yönetilen arabirimler aracılığıyla açığa çıkarılan üyelere erişme  
 <xref:System.Windows.Forms.HtmlDocument>ve <xref:System.Windows.Forms.HtmlElement> açığa çıkarılan üyelere erişimi etkinleştiren dört yöntem sağlar. Aşağıdaki tabloda türler ve bunlara karşılık gelen Yöntemler gösterilmektedir.  
  
|Üye Türü|Yöntem (ler)|  
|-----------------|-----------------|  
|Özellikler (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Yöntemler|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Olaylar (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Olaylar (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Olaylar (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Bu yöntemleri kullandığınızda, doğru temel alınan türdeki bir öğeye sahip olduğunuz varsayılır. Bir HTML sayfasındaki bir `Submit` `FORM` öğenin olayını dinlemek istediğinizi varsayalım, böylece kullanıcı bunları sunucuya göndermeden önce değerler üzerinde `FORM`bazı ön işlemler gerçekleştirebilirsiniz. İdeal olarak, HTML üzerinde denetiminiz varsa, öğesini benzersiz `FORM` `ID` bir özniteliğe sahip olacak şekilde tanımlayın.  
  
```html  
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
  
 Bu sayfayı <xref:System.Windows.Forms.WebBrowser> denetime yükledikten sonra, bağımsız değişken olarak kullanarak `form1` çalışma zamanını almak <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> `FORM` için yöntemini kullanabilirsiniz.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Yönetilmeyen arabirimlere erişme  
 Ayrıca, yönetilen HTML DOM üzerinde gösterilmeyen üyelere, her DOM sınıfının açığa çıkarılan yönetilmeyen bileşen nesne modeli (COM) arabirimlerini kullanarak erişebilirsiniz. Bu, açığa çıkarılan üyelere karşı birkaç çağrı yapmanız gerekiyorsa veya gösterilmeyen Üyeler yönetilen HTML DOM tarafından sarmalanmamış diğer yönetilmeyen arabirimleri geri döndürmediğinde bu önerilir.  
  
 Aşağıdaki tabloda, yönetilen HTML DOM aracılığıyla kullanıma sunulan yönetilmeyen arabirimlerin hepsi gösterilmektedir. Kullanım açıklaması ve örneğin kodu için her bir bağlantıya tıklayın.  
  
|Tür|Yönetilmeyen arabirim|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 COM arabirimlerini kullanmanın en kolay yolu, yönetilmeyen HTML DOM kitaplığı 'na (MSHTML. dll) bir başvuru eklemektir, ancak bu desteklenmez. Daha fazla bilgi için bkz. [Bilgi Bankası makalesi 934368](https://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>Betik Işlevlerine erişme  
 HTML sayfası, JScript veya VBScript gibi bir betik dilini kullanarak bir veya daha fazla işlevi tanımlayabilir. Bu işlevler sayfadaki bir `SCRIPT` sayfanın içine yerleştirilir ve isteğe bağlı olarak ya da Dom üzerindeki bir olaya yanıt olarak çalıştırılabilir.  
  
 <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> Yöntemini kullanarak HTML sayfasında tanımladığınız herhangi bir betik işlevini çağırabilirsiniz. Betik yöntemi bir HTML öğesi döndürürse, bu dönüş sonucunu bir <xref:System.Windows.Forms.HtmlElement>olarak dönüştürmek için bir atama kullanabilirsiniz. Ayrıntılar ve örnek kod için bkz <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen HTML Belgesi Nesne Modelini Kullanma](using-the-managed-html-document-object-model.md)
