---
title: My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: caddad463f7c525c8b715d70f49bf8bebcc7cfbd
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701258"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme (Visual Basic)

Bu konuda, projenizin `_MYTYPE` koşullu derleme sabitini ayarlanarak hangi `My` nesnelerinin etkinleştirildiğini nasıl denetleyebileceğinizi açıklanmaktadır. Visual Studio tümleşik geliştirme ortamı (IDE) proje türüyle eşitlenmiş bir proje için `_MYTYPE` koşullu derleme sabiti tutar.  
  
## <a name="predefined-_mytype-values"></a>Önceden tanımlanmış \_MYTYPE değerleri  

@No__t-1 koşullu derleme sabitini ayarlamak için `/define` derleyici seçeneğini kullanmanız gerekir. @No__t-0 sabiti için kendi değerini belirtirken, dize değerini ters eğik çizgi/tırnak işareti (\\ ") sıralarında almalısınız. Örneğin, şunu kullanabilirsiniz:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Bu tabloda, `_MYTYPE` koşullu derleme sabitinin çeşitli proje türleri için nasıl ayarlandığı gösterilmektedir.  
  
|Proje türü|\_MYTYPE değeri|  
|------------------|--------------------|  
|Sınıf Kitaplığı|Pencerelerin|  
|Konsol Uygulaması|Konsola|  
|Web|Web|  
|Web Denetim Kitaplığı|'Dan|  
|Windows uygulaması|WindowsForms|  
|Windows uygulaması, özel @no__t ile Başlarken-0|"WindowsFormsWithCustomSubMain"|  
|Windows Denetim Kitaplığı|Pencerelerin|  
|Windows Hizmeti|Konsola|  
|olmamalıdır|Olmamalıdır|  
  
> [!NOTE]
> Tüm koşullu derleme dizesi karşılaştırmaları, `Option Compare` ifadesinin nasıl ayarlandığına bakılmaksızın büyük/küçük harfe duyarlıdır.  
  
## <a name="dependent-_my-compilation-constants"></a>Bağımlı \_MY derleme sabitleri  

@No__t-0 koşullu derleme sabiti, daha farklı `_MY` derleme sabitlerinin değerlerini denetler:  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|Konsola|Konsola|Pencerelerin|tanımlayan|Pencerelerin|TRUE|  
|Özel|tanımlayan|tanımlayan|tanımlayan|tanımlayan|tanımlayan|  
|Olmamalıdır|tanımlayan|tanımlayan|tanımlayan|tanımlayan|tanımlayan|  
|Web|tanımlayan|Web|YANLÝÞ|Web|YANLÝÞ|  
|'Dan|tanımlayan|Web|YANLÝÞ|Web|TRUE|  
|"Windows" veya ""|Pencerelerin|Pencerelerin|tanımlayan|Pencerelerin|TRUE|  
|WindowsForms|WindowsForms|Pencerelerin|TRUE|Pencerelerin|TRUE|  
|"WindowsFormsWithCustomSubMain"|Konsola|Pencerelerin|TRUE|Pencerelerin|TRUE|  
  
 Varsayılan olarak, tanımsız koşullu derleme sabitleri `FALSE` ' a çözümlenir. Varsayılan davranışı geçersiz kılmak için projenizi derlerken tanımsız sabitler için değerler belirtebilirsiniz.  
  
> [!NOTE]
> @No__t-0 "Custom" olarak ayarlandığında, proje `My` ad alanını içerir, ancak nesne içermez. Ancak, `_MYTYPE` ' ı "Empty" olarak ayarlamak derleyicinin `My` ad alanını ve nesnelerini eklemesini önler.  
  
 Bu tablo `_MY` derleme sabitlerinin önceden tanımlanmış değerlerinin etkilerini açıklar.  
  
|Sabit|Açıklama|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Sabit "Console," Windows "veya" WindowsForms "ise `My.Application` ' ı etkinleştirilir:<br /><br /> -"Console" sürümü <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> ' dan türetilir. ve "Windows" sürümünden daha az üye içeriyor.<br />-"Windows" sürümü @no__t -0 öğesinden türetilir ve "WindowsForms" sürümünden daha az üyeye sahiptir.<br />-@No__t-0 ' ın "WindowsForms" sürümü <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> ' den türetilir. @No__t-0 sabiti "winexe" olarak tanımlanmışsa, sınıf bir `Sub Main` yöntemi içerir.|  
|`_MYCOMPUTERTYPE`|Sabit "Web" veya "Windows" ise `My.Computer` ' ı etkinleştirilir:<br /><br /> -"Web" sürümü <xref:Microsoft.VisualBasic.Devices.ServerComputer> ' dan türetilir ve "Windows" sürümünden daha az üyeye sahiptir.<br />-@No__t-0 ' ın "Windows" sürümü <xref:Microsoft.VisualBasic.Devices.Computer> ' den türetilir.|  
|`_MYFORMS`|Sabit `TRUE` ise `My.Forms` ' ı etkinleştirilir.|  
|`_MYUSERTYPE`|Sabit "Web" veya "Windows" ise `My.User` ' ı etkinleştirilir:<br /><br /> -@No__t-0 ' ın "Web" sürümü geçerli HTTP isteğinin kullanıcı kimliğiyle ilişkili.<br />-@No__t-0 ' ın "Windows" sürümü iş parçacığının geçerli sorumlusu ile ilişkili.|  
|`_MYWEBSERVICES`|Sabit `TRUE` ise `My.WebServices` ' ı etkinleştirilir.|  
|`_MYTYPE`|Sabit "Web" ise `My.Log`, `My.Request` ve `My.Response` ' yi etkinleştirilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My Özellikleri Proje Türüne Nasıl Bağımlıdır](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response Nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
