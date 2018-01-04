---
title: "Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97a795930eb6965bd0ed15254969a72f45700306
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme
Yönetilen HTML belgesi nesne modeli (DOM) adlı bir sınıf içerir <xref:System.Windows.Forms.HtmlElement> özellikleri, yöntemleri ve tüm HTML öğeleri ortak olan olayları gösterir. Bazı durumlarda, ancak, yönetilen arabirimi değil doğrudan kullanıma üyelere erişmek gerekecektir. Bu konuda da dahil olmak üzere gösterilmeyen üyelere erişme için iki yolla inceler [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] ve bir Web sayfası içinde tanımlanan VBScript işlevleri.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Yönetilen arabirimleri aracılığıyla gösterilmeyen üyelere erişme  
 <xref:System.Windows.Forms.HtmlDocument>ve <xref:System.Windows.Forms.HtmlElement> gösterilmeyen erişmesini dört yöntemleri sağlar. Aşağıdaki tabloda, türlerini ve bunların karşılık gelen yöntemleri gösterir.  
  
|Üye Türü|Yöntemleri|  
|-----------------|-----------------|  
|Özellikler (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Yöntemler|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Olaylar (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Olaylar (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Olaylar (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Bu yöntemleri kullandığınızda, doğru temel türünde bir öğe sahip olduğunuz varsayılır. Dinlemek istediğinizi varsayalım `Submit` olayı bir `FORM` bir HTML öğesindeki sayfası, böylece üzerinde bazı ön işleme gerçekleştirebilirsiniz `FORM`ait kullanıcı bunları sunucuya göndermeden önce değerleri. İdeal olarak, HTML üzerinde denetim varsa, tanımlayın `FORM` benzersiz olmasını `ID` özniteliği.  
  
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
  
 Bu sayfaya yükledikten sonra <xref:System.Windows.Forms.WebBrowser> kullanabileceğiniz denetimi <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> alma yöntemi `FORM` çalıştırma kullanarak `form1` bağımsız değişkeni olarak.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Yönetilmeyen arabirimler erişme  
 Yönetilen HTML DOM gösterilmeyen her DOM sınıfı tarafından kullanıma sunulan yönetilmeyen Bileşen Nesne Modeli (COM) arabirimlerini kullanarak da erişebilirsiniz. Bu gösterilmeyen karşı birkaç çağrı yapmak varsa veya gösterilmeyen yönetilen HTML DOM tarafından Sarmalanan olmayan diğer yönetilmeyen arabirimler döndürürse önerilir.  
  
 Aşağıdaki tabloda tüm yönetilen HTML DOM kullanıma sunulan yönetilmeyen arabirimler gösterir Her bağlantı kullanımı ve örnek kod bir açıklama için tıklayın.  
  
|Tür|Yönetilmeyen arabirimi|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 Bu desteklenmeyen olsa COM arabirimleri kullanmak için en kolay yolu, uygulamanızdan (MSHTML.dll) yönetilmeyen HTML DOM kitaplığına bir başvuru eklemektir. Daha fazla bilgi için bkz: [Bilgi Bankası makalesi 934368](http://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>Komut dosyası işlevleri erişme  
 HTML sayfası gibi bir komut dosyası dili kullanarak bir veya daha fazla işlevleri tanımlayabilirsiniz [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] veya VBScript. Bu işlevler içine yerleştirilen bir `SCRIPT` sayfasında sayfasında ve isteğe bağlı veya bir olaya yanıt olarak DOM üzerinde çalıştırılabilir  
  
 Tanımladığınız kullanılarak bir HTML sayfasında herhangi bir komut dosyası işlevleri çağırabilir <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> yöntemi. Komut dosyası yöntemi bir HTML öğesi döndürürse, bu dönüş sonucu dönüştürmek için bir cast kullanabilirsiniz bir <xref:System.Windows.Forms.HtmlElement>. Ayrıntılar ve kod örneği için bkz: <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen HTML Belgesi Nesne Modelini Kullanma](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
