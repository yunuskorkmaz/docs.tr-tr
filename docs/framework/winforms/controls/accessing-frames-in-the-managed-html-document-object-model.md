---
title: Yönetilen HTML Belgesi Nesne Modelindeki Çerçevelere Erişme
ms.date: 03/30/2017
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
ms.openlocfilehash: b48a93cef2ea8fd2d39f58d8f458c4b287a10154
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207514"
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a>Yönetilen HTML Belgesi Nesne Modelindeki Çerçevelere Erişme
Bazı HTML belgeleri çıkışı oluşur *çerçeveleri*, ya da kendi ayrı HTML belgeleri tutabilir windows. Çerçeveler kullanarak diğer çerçeveler sürekli içeriklerini değiştirme sırasında bir veya daha fazla parça sayfasının bir gezinti çubuğu gibi statik kalır HTML sayfaları oluşturmak kolaylaştırır.  
  
 HTML yazarlarının çerçeveler iki yoldan biriyle oluşturabilirsiniz:  
  
-   Kullanarak `FRAMESET` ve `FRAME` sabit pencerelerini etiketler.  
  
 veya  
  
-   Kullanarak `IFRAME` çalışma zamanında konumlandırılmasına kayan bir pencere oluşturur etiketi.  
  
1.  Çerçeve HTML belgeleri içerdiğinden, bunlar belge nesne modeli (DOM) pencere öğeleri ve çerçeve öğeler temsil edilir.  
  
2.  Eriştiğinizde bir `FRAME` veya `IFRAME` çerçeveler koleksiyonunu kullanarak etiketi <xref:System.Windows.Forms.HtmlWindow>, çerçeveye karşılık gelen pencere öğesi alınıyor. Bu özelliklerin tümü çerçevenin dinamik, geçerli URL, belge ve boyutu gibi temsil eder.  
  
3.  Eriştiğinizde bir `FRAME` veya `IFRAME` kullanarak etiketi <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> özelliği <xref:System.Windows.Forms.HtmlWindow>, <xref:System.Windows.Forms.HtmlElement.Children%2A> koleksiyonu veya gibi yöntemler <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> veya <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, çerçeve öğesi alınıyor. Bu, özgün HTML dosyasında belirtilen URL gibi çerçeve statik özelliklerini temsil eder.  
  
## <a name="frames-and-security"></a>Çerçeve ve güvenlik  
 Yönetilen HTML DOM olarak bilinen bir güvenlik önlemi uygulayan olgu tarafından çerçeveler erişimi karmaşık *çerçeveler arası komut dosyası güvenlik*. Bir belge içeriyorsa bir `FRAMESET` iki veya daha fazla ile `FRAME`s farklı etki alanlarında, bunlar `FRAME`s birbiriyle çalışamazsınız. Diğer bir deyişle, bir `FRAME` Web sitesinden görüntüler içerik bilgilerinde erişemiyor bir `FRAME` gibi bir üçüncü taraf site sunan http://www.adatum.com/. Bu güvenlik düzeyinde uygulanır <xref:System.Windows.Forms.HtmlWindow> sınıfı. Hakkında genel bilgi edinebilirsiniz bir `FRAME` URL'sini, ancak gibi başka bir Web sitesi barındırma erişemiyor olacaktır, <xref:System.Windows.Forms.HtmlWindow.Document%2A> veya boyutu ya da kendi barındırma konumu değiştirmek `FRAME` veya `IFRAME`.  
  
 Bu kuralı kullanarak açın windows için de geçerlidir <xref:System.Windows.Forms.HtmlWindow.Open%2A> ve <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> yöntemleri. Açtığınız pencere barındırılan sayfasından farklı bir etki alanında ise <xref:System.Windows.Forms.WebBrowser> denetimi, olmayacak bu pencereyi taşıyabilir veya içeriğini inceleyin. Kullanıyorsanız bu kısıtlamaları da zorlanır <xref:System.Windows.Forms.WebBrowser> Windows Forms tabanlı uygulamanızı dağıtmak için kullanılan Web sitesinden farklı bir Web sitesini görüntülemek için denetim. Kullanırsanız [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] uygulamanız bir Web sitesinden ve yüklemek için dağıtım teknolojisini kullanan <xref:System.Windows.Forms.WebBrowser> Web sitesini B görüntülemek için access Web sitesinin B'nin veri mümkün olmaz.  
  
 Siteler arası komut dosyası hakkında daha fazla bilgi için bkz: [hakkında çerçeveler arası komut dosyası oluşturma ve güvenlik](http://msdn.microsoft.com/library/ms533028.aspx).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ÇERÇEVE öğesi &#124; nesne çerçeve](http://msdn.microsoft.com/library/ms535250.aspx)  
 [Yönetilen HTML Belgesi Nesne Modelini Kullanma](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
