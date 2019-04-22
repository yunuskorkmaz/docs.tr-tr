---
title: My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: c0b47521c6a62071466ae4193cd8553bdfb3dcde
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58890377"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme (Visual Basic)

Bu konuda, nasıl denetleyebileceğiniz açıklanmaktadır `My` nesneleri projenizin ayarlayarak etkin `_MYTYPE` koşullu derleme sabiti. Visual Studio tümleşik geliştirme ortamı (IDE) tutar `_MYTYPE` koşullu derleme sabiti için projenin tipini ile eşitlenmiş bir proje.  
  
## <a name="predefined-mytype-values"></a>Önceden tanımlanmış \_MYTYPE değerleri  

Kullanmalısınız `/define` ayarlamak için derleyici seçeneği `_MYTYPE` koşullu derleme sabiti. Kendi değerinizi belirtirken `_MYTYPE` sabiti, dize değeri ters eğik çizgi/tırnak işareti içine almanız gerekir (\\") dizileri. Örneğin, aşağıdaki kullanabilirsiniz:  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Bu tabloda neler gösterilir `_MYTYPE` koşullu derleme sabiti ayarlandığında birkaç proje türleri için.  
  
|Proje türü|\_MYTYPE değeri|  
|------------------|--------------------|  
|Sınıf Kitaplığı|"Windows"|  
|Konsol Uygulaması|"Konsol"|  
|Web|"Web"|  
|Web Denetim Kitaplığı|"WebControl"|  
|Windows uygulama|"WindowsForms"|  
|Windows özel başlatma sırasında uygulama `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Windows Denetim Kitaplığı|"Windows"|  
|Windows Hizmeti|"Konsol"|  
|boş|"Boş"|  
  
> [!NOTE]
> Tüm koşullu derleme dize karşılaştırmaları bağımsız olarak nasıl, küçük harf duyarlıdır `Option Compare` deyimi ayarlanır.  
  
## <a name="dependent-my-compilation-constants"></a>Bağımlı \_MY derleme sabitleri  

`_MYTYPE` Koşullu derleme sabitini birkaç farklı değerleri sırayla denetler `_MY` derleme sabitleri:  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Konsol"|"Konsol"|"Windows"|Tanımlanmadı|"Windows"|TRUE|  
|"Özel"|Tanımlanmadı|Tanımlanmadı|Tanımlanmadı|Tanımlanmadı|Tanımlanmadı|  
|"Boş"|Tanımlanmadı|Tanımlanmadı|Tanımlanmadı|Tanımlanmadı|Tanımlanmadı|  
|"Web"|Tanımlanmadı|"Web"|FALSE|"Web"|FALSE|  
|"WebControl"|Tanımlanmadı|"Web"|FALSE|"Web"|TRUE|  
|"Windows" veya ""|"Windows"|"Windows"|Tanımlanmadı|"Windows"|TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|"Konsol"|"Windows"|TRUE|"Windows"|TRUE|  
  
 Varsayılan olarak, tanımsız koşullu derleme sabitleri çözümlemek için `FALSE`. Varsayılan davranışı geçersiz kılmak için proje derlenirken tanımlanmamış sabit değerleri belirtebilirsiniz.  
  
> [!NOTE]
> Zaman `_MYTYPE` ayarlanmış "Özel", projeyi içeren `My` ad alanı, ancak hiçbir nesne içerir. Ancak, ayarı `_MYTYPE` için "Boş" engeller derleyici eklemesini `My` ad alanı ve nesneleri.  
  
 Bu tablo önceden tanımlanmış değerler etkilerini açıklar `_MY` derleme sabitleri.  
  
|Sabit|Açıklama|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Sağlar `My.Application`, sabit "Konsolunda, Windows," ise "veya"WindowsForms":<br /><br /> -"Konsol" sürümü türetildiği <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. ve "Windows" belirtilenden daha az sayıda üye vardır.<br />-"Windows" sürüm türetildiği <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>.ve "WindowsForms" belirtilenden daha az sayıda üye vardır.<br />-"WindowsForms" sürümünü `My.Application` türetildiği <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Varsa `TARGET` sabiti "winexe" olacak şekilde tanımlandı ve sınıf içeren bir `Sub Main` yöntemi.|  
|`_MYCOMPUTERTYPE`|Sağlar `My.Computer`, sabit "Web" veya "Windows" ise:<br /><br /> -"Web'de" sürüm türetildiği <xref:Microsoft.VisualBasic.Devices.ServerComputer>, ve "Windows" belirtilenden daha az sayıda üye vardır.<br />-"Windows" sürümünü `My.Computer` türetildiği <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Sağlar `My.Forms`sabittir, `TRUE`.|  
|`_MYUSERTYPE`|Sağlar `My.User`, sabit "Web" veya "Windows" ise:<br /><br /> -"Web'de" sürümünü `My.User` geçerli HTTP isteği kullanıcı kimliğiyle ilişkilendirilir.<br />-"Windows" sürümünü `My.User` iş parçacığının geçerli sorumlu ile ilişkilidir.|  
|`_MYWEBSERVICES`|Sağlar `My.WebServices`sabittir, `TRUE`.|  
|`_MYTYPE`|Sağlar `My.Log`, `My.Request`, ve `My.Response`, "Web" sabittir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My Özellikleri Proje Türüne Nasıl Bağımlıdır](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response Nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
