---
title: My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: b06e71784a4d02bcbcd755d14e57ef88c4322f7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592164"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme (Visual Basic)
Bu konuda, hangi denetim nasıl açıklanmaktadır `My` nesneleri projenizin ayarlayarak etkin `_MYTYPE` koşullu derleme sabiti. Visual Studio tümleşik geliştirme ortamı (IDE) tutar `_MYTYPE` proje türü ile eşitlenmiş bir proje için koşullu derleme sabiti.  
  
## <a name="predefined-mytype-values"></a>Önceden tanımlanmış _MYTYPE değerleri  
 Kullanmalısınız `/define` ayarlamak için derleyici seçeneği `_MYTYPE` koşullu derleme sabiti. İçin kendi değer belirtirken `_MYTYPE` sabit, dize değeri ters eğik çizgi/tırnak işareti içine almanız gerekir (\\") sıraları. Örneğin, kullanabilirsiniz:  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Bu tablo hangi gösterir `_MYTYPE` koşullu derleme sabiti ayarlanmış birkaç türleri proje için.  
  
|Proje türü|_MYTYPE değeri|  
|------------------|--------------------|  
|Sınıf Kitaplığı|"Windows"|  
|Konsol Uygulaması|"Konsol"|  
|Web|"Web"|  
|Web Denetim Kitaplığı|"WebControl"|  
|Windows uygulaması|"Windows Forms"|  
|Windows özel başlatılırken uygulama `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Windows Denetim Kitaplığı|"Windows"|  
|Windows Hizmeti|"Konsol"|  
|boş|"Boş"|  
  
> [!NOTE]
>  Tüm koşullu derleme dize karşılaştırmaları bağımsız olarak nasıl, küçük harf duyarlıdır `Option Compare` deyimi ayarlanır.  
  
## <a name="dependent-my-compilation-constants"></a>Bağımlı _MY derleme sabitleri  
 `_MYTYPE` Koşullu derleme sabiti sırayla birkaç diğer değerlerini denetimleri `_MY` derleme sabitleri:  
  
|_MYTYPE|_MYAPPLICATIONTYPE|_MYCOMPUTERTYPE|_MYFORMS|_MYUSERTYPE|_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Konsol"|"Konsol"|"Windows"|Tanımlanmamış|"Windows"|TRUE|  
|"Özel"|Tanımlanmamış|Tanımlanmamış|Tanımlanmamış|Tanımlanmamış|Tanımlanmamış|  
|"Boş"|Tanımlanmamış|Tanımlanmamış|Tanımlanmamış|Tanımlanmamış|Tanımlanmamış|  
|"Web"|Tanımlanmamış|"Web"|FALSE|"Web"|FALSE|  
|"WebControl"|Tanımlanmamış|"Web"|FALSE|"Web"|TRUE|  
|"Windows" veya ""|"Windows"|"Windows"|Tanımlanmamış|"Windows"|TRUE|  
|"Windows Forms"|"Windows Forms"|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|"Konsol"|"Windows"|TRUE|"Windows"|TRUE|  
  
 Varsayılan olarak, tanımlanmamış koşullu derleme sabitleri çözümlemek için `FALSE`. Varsayılan davranışı geçersiz kılma projenizi derlerken tanımsız sabitleri değerlerini belirtebilirsiniz.  
  
> [!NOTE]
>  Zaman `_MYTYPE` ayarlanır "Özel" projeyi içeren `My` ad alanı, ancak hiçbir nesne içerir. Ancak, ayarı `_MYTYPE` için "Boş" engeller derleyici eklemelerini `My` ad alanı ve nesnelerini.  
  
 Bu tablo önceden tanımlanmış değerler etkilerini açıklar `_MY` derleme sabitleri.  
  
|Sabit|Açıklama|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Etkinleştirir `My.Application`, sabit "Konsolu, Windows," ise "veya"Windows Forms":<br /><br /> -"Konsol" sürüm türetilen <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. ve "Windows" sürümden daha az sayıda üye sahiptir.<br />-"Windows" sürüm türetilen <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>.ve "Windows Forms" sürümden daha az sayıda üye içeriyor.<br />-"Windows Forms" sürümünü `My.Application` türetilen <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Varsa `TARGET` sabiti "winexe" olarak tanımlanır ve ardından sınıfı içeren bir `Sub Main` yöntemi.|  
|`_MYCOMPUTERTYPE`|Etkinleştirir `My.Computer`, sabit "Web" veya "Windows" ise:<br /><br /> -"Web" sürümü türetilen <xref:Microsoft.VisualBasic.Devices.ServerComputer>, ve "Windows" sürümden daha az sayıda üye sahiptir.<br />-"Windows" sürümünü `My.Computer` türetilen <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Etkinleştirir `My.Forms`, sabit ise `TRUE`.|  
|`_MYUSERTYPE`|Etkinleştirir `My.User`, sabit "Web" veya "Windows" ise:<br /><br /> -"Web" sürümünü `My.User` geçerli HTTP isteği kullanıcı kimliğiniz ile ilişkili.<br />-"Windows" sürümünü `My.User` iş parçacığının geçerli sorumlu ile ilişkilidir.|  
|`_MYWEBSERVICES`|Etkinleştirir `My.WebServices`, sabit ise `TRUE`.|  
|`_MYTYPE`|Etkinleştirir `My.Log`, `My.Request`, ve `My.Response`, sabit "Web" ise.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [My Özellikleri Proje Türüne Nasıl Bağımlıdır](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [My.Response Nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
