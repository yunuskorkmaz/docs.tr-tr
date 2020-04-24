---
title: My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: 0387aca08e3a31b0a2045369919894d88caf5b76
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330324"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme (Visual Basic)

Bu konuda, projenizin `My` `_MYTYPE` koşullu derleme sabitini ayarlanarak hangi nesnelerin etkinleştirildiğini nasıl denetleyebileceğinizi açıklanmaktadır. Visual Studio tümleşik geliştirme ortamı (IDE) proje türüyle eşitlenmiş `_MYTYPE` bir proje için koşullu derleme sabitini tutar.  
  
## <a name="predefined-_mytype-values"></a>Önceden \_tanımlanmış MyType değerleri  

Koşullu derleme sabitini ayarlamak `/define` için derleyici seçeneğini kullanmanız gerekir. `_MYTYPE` `_MYTYPE` Sabit için kendi değerini belirtirken, dize değerini ters eğik çizgi/tırnak işareti (\\") sıralarında almalısınız. Örneğin, şunu kullanabilirsiniz:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Bu tablo, `_MYTYPE` koşullu derleme sabitinin çeşitli proje türleri için ne şekilde ayarlandığını gösterir.  
  
|Proje türü|\_MYTYPE değeri|  
|------------------|--------------------|  
|Sınıf Kitaplığı|Pencerelerin|  
|Konsol Uygulaması|Konsola|  
|Web|Web|  
|Web Denetim Kitaplığı|'Dan|  
|Windows uygulaması|WindowsForms|  
|Windows uygulaması, özel ile Başlarken`Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Windows Denetim Kitaplığı|Pencerelerin|  
|Windows Hizmeti|Konsola|  
|Olmamalıdır|Olmamalıdır|  
  
> [!NOTE]
> Tüm koşullu derleme dizesi karşılaştırmaları, `Option Compare` deyimin nasıl ayarlandığına bakılmaksızın büyük/küçük harfe duyarlıdır.  
  
## <a name="dependent-_my-compilation-constants"></a>Bağımlı \_derleme sabitlerim  

`_MYTYPE` Koşullu derleme sabiti, sırasıyla diğer `_MY` birçok derleme sabitlerinin değerlerini denetler:  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|Konsola|Konsola|Pencerelerin|Tanımlayan|Pencerelerin|TRUE|  
|Özel|Tanımlayan|Tanımlayan|Tanımlayan|Tanımlayan|Tanımlayan|  
|Olmamalıdır|Tanımlayan|Tanımlayan|Tanımlayan|Tanımlayan|Tanımlayan|  
|Web|Tanımlayan|Web|FALSE|Web|FALSE|  
|'Dan|Tanımlayan|Web|FALSE|Web|TRUE|  
|"Windows" veya ""|Pencerelerin|Pencerelerin|Tanımlayan|Pencerelerin|TRUE|  
|WindowsForms|WindowsForms|Pencerelerin|TRUE|Pencerelerin|TRUE|  
|"WindowsFormsWithCustomSubMain"|Konsola|Pencerelerin|TRUE|Pencerelerin|TRUE|  
  
 Varsayılan olarak, tanımsız koşullu derleme sabitleri olarak `FALSE`çözümlenir. Varsayılan davranışı geçersiz kılmak için projenizi derlerken tanımsız sabitler için değerler belirtebilirsiniz.  
  
> [!NOTE]
> `_MYTYPE` "Custom" olarak ayarlandığında, proje `My` ad alanını içerir, ancak nesne içermez. Ancak, " `_MYTYPE` Empty" olarak ayarlandığında derleyicinin `My` ad alanını ve nesnelerini eklemesini önler.  
  
 Bu tabloda, `_MY` derleme sabitlerinin önceden tanımlanmış değerlerinin etkileri açıklanmaktadır.  
  
|Sabit|Anlamı|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Sabit `My.Application`"konsol," Windows "veya" WindowsForms "ise, etkinleştirilir:<br /><br /> -"Konsol" sürümü öğesinden <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>türetilir. ve "Windows" sürümünden daha az üye içeriyor.<br />-"Windows" sürümü öğesinden <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>türetilir. ve "WindowsForms" sürümünden daha az üye içeriyor.<br />-"WindowsForms" sürümü öğesinden `My.Application` <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>türetilir. `TARGET` Sabit "winexe" olarak tanımlanmışsa, sınıf bir `Sub Main` yöntemi içerir.|  
|`_MYCOMPUTERTYPE`|, `My.Computer`Sabit "Web" veya "Windows" ise izin vermez:<br /><br /> -"Web" sürümü öğesinden <xref:Microsoft.VisualBasic.Devices.ServerComputer>türetilir ve "Windows" sürümünden daha az üyeye sahiptir.<br />-"Windows" sürümü, öğesinden `My.Computer` <xref:Microsoft.VisualBasic.Devices.Computer>türetilir.|  
|`_MYFORMS`|Sabit `My.Forms`ise, etkinleştirilir `TRUE`.|  
|`_MYUSERTYPE`|, `My.User`Sabit "Web" veya "Windows" ise izin vermez:<br /><br /> -"Web" sürümü `My.User` geçerli http isteğinin kullanıcı kimliğiyle ilişkili.<br />-"Windows" sürümü `My.User` , iş parçacığının geçerli sorumlusu ile ilişkilendirilmiştir.|  
|`_MYWEBSERVICES`|Sabit `My.WebServices`ise, etkinleştirilir `TRUE`.|  
|`_MYTYPE`|,, Ve `My.Response`sabiti "Web" ise etkinleştirilir. `My.Log` `My.Request`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My Özellikleri Proje Türüne Nasıl Bağımlıdır](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-tanımla (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response Nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
