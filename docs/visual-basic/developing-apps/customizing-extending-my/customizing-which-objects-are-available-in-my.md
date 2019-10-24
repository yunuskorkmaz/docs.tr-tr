---
title: My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: bb3f8eb2e8b1cf5bce364fc4b3ce0587769bb5f9
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775207"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme (Visual Basic)

Bu konuda, projenizin `_MYTYPE` koşullu derleme sabiti ayarlanarak hangi `My` nesnelerinin etkinleştirildiğini nasıl denetleyebileceği açıklanmaktadır. Visual Studio tümleşik geliştirme ortamı (IDE) proje türüyle eşitlenmiş bir proje için `_MYTYPE` koşullu derleme sabiti tutar.  
  
## <a name="predefined-_mytype-values"></a>Önceden tanımlanmış \_MYTYPE değerleri  

@No__t_1 koşullu derleme sabitini ayarlamak için `/define` derleyici seçeneğini kullanmanız gerekir. @No__t_0 sabiti için kendi değerini belirtirken, dize değerini ters eğik çizgi/tırnak işareti (\\ ") sıralarında almalısınız. Örneğin, şunu kullanabilirsiniz:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Bu tabloda, `_MYTYPE` koşullu derleme sabitinin çeşitli proje türleri için ne şekilde ayarlandığı gösterilmektedir.  
  
|Proje türü|\_MYTYPE değeri|  
|------------------|--------------------|  
|Sınıf Kitaplığı|Pencerelerin|  
|Konsol Uygulaması|Konsola|  
|Web|Web|  
|Web Denetim Kitaplığı|'Dan|  
|Windows uygulaması|WindowsForms|  
|Windows uygulaması, özel `Sub Main` ile Başlarken|"WindowsFormsWithCustomSubMain"|  
|Windows Denetim Kitaplığı|Pencerelerin|  
|Windows Hizmeti|Konsola|  
|Olmamalıdır|Olmamalıdır|  
  
> [!NOTE]
> Tüm koşullu derleme dizesi karşılaştırmaları, `Option Compare` deyimin nasıl ayarlandığına bakılmaksızın büyük/küçük harfe duyarlıdır.  
  
## <a name="dependent-_my-compilation-constants"></a>Bağımlı \_MY derleme sabitleri  

Koşullu derleme sabiti `_MYTYPE`, diğer `_MY` derleme sabitlerinin değerlerini denetler:  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|Konsola|Konsola|Pencerelerin|Tanımlayan|Pencerelerin|TRUE|  
|Özel|Tanımlayan|Tanımlayan|Tanımlayan|Tanımlayan|Tanımlayan|  
|Olmamalıdır|Tanımlayan|Tanımlayan|Tanımlayan|Tanımlayan|Tanımlayan|  
|Web|Tanımlayan|Web|YANLÝÞ|Web|YANLÝÞ|  
|'Dan|Tanımlayan|Web|YANLÝÞ|Web|TRUE|  
|"Windows" veya ""|Pencerelerin|Pencerelerin|Tanımlayan|Pencerelerin|TRUE|  
|WindowsForms|WindowsForms|Pencerelerin|TRUE|Pencerelerin|TRUE|  
|"WindowsFormsWithCustomSubMain"|Konsola|Pencerelerin|TRUE|Pencerelerin|TRUE|  
  
 Varsayılan olarak, tanımsız koşullu derleme sabitleri `FALSE` olarak çözümlenir. Varsayılan davranışı geçersiz kılmak için projenizi derlerken tanımsız sabitler için değerler belirtebilirsiniz.  
  
> [!NOTE]
> @No__t_0 "Custom" olarak ayarlandığında, proje `My` ad alanını içerir, ancak nesne içermez. Ancak, `_MYTYPE` "Empty" olarak ayarlamak derleyicinin `My` ad alanını ve nesnelerini eklemesini engeller.  
  
 Bu tabloda `_MY` derleme sabitlerinin önceden tanımlanmış değerlerinin etkileri açıklanmaktadır.  
  
|Sabit|Açıklama|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Sabit "Console," Windows "veya" WindowsForms "ise `My.Application` etkinleştirilir:<br /><br /> -"Console" sürümü <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> türetilir. ve "Windows" sürümünden daha az üye içeriyor.<br />-"Windows" sürümü <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> türetilir. ve "WindowsForms" sürümünden daha az üye içeriyor.<br />-@No__t_0 "WindowsForms" sürümü <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> türetilir. @No__t_0 sabiti "winexe" olarak tanımlanmışsa, sınıf bir `Sub Main` yöntemi içerir.|  
|`_MYCOMPUTERTYPE`|Sabit "Web" veya "Windows" ise `My.Computer` etkinleştirilir:<br /><br /> -"Web" sürümü <xref:Microsoft.VisualBasic.Devices.ServerComputer> türetilir ve "Windows" sürümünden daha az üyeye sahiptir.<br />-@No__t_0 "Windows" sürümü <xref:Microsoft.VisualBasic.Devices.Computer> türetilir.|  
|`_MYFORMS`|Sabit `TRUE` `My.Forms` etkinleştirilir.|  
|`_MYUSERTYPE`|Sabit "Web" veya "Windows" ise `My.User` etkinleştirilir:<br /><br /> -@No__t_0 "Web" sürümü geçerli HTTP isteğinin kullanıcı kimliğiyle ilişkili.<br />-@No__t_0 "Windows" sürümü iş parçacığının geçerli sorumlusu ile ilişkili.|  
|`_MYWEBSERVICES`|Sabit `TRUE` `My.WebServices` etkinleştirilir.|  
|`_MYTYPE`|@No__t_0, `My.Request` ve `My.Response`, sabit "Web" ise izin vermez.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My Özellikleri Proje Türüne Nasıl Bağımlıdır](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-tanımla (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response Nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
