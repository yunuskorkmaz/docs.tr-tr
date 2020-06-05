---
title: My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: 5245c129281bc8c7c1c6fe9215a221889380a901
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410224"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme (Visual Basic)

Bu konuda, `My` projenizin koşullu derleme sabitini ayarlanarak hangi nesnelerin etkinleştirildiğini nasıl denetleyebileceğinizi açıklanmaktadır `_MYTYPE` . Visual Studio tümleşik geliştirme ortamı (IDE) proje `_MYTYPE` türüyle eşitlenmiş bir proje için koşullu derleme sabitini tutar.  
  
## <a name="predefined-_mytype-values"></a>Önceden tanımlanmış \_ MyType değerleri  

`/define`Koşullu derleme sabitini ayarlamak için derleyici seçeneğini kullanmanız gerekir `_MYTYPE` . Sabit için kendi değerini belirtirken `_MYTYPE` , dize değerini ters eğik çizgi/tırnak işareti ( \\ ") sıralarında almalısınız. Örneğin, şunu kullanabilirsiniz:  
  
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
> Tüm koşullu derleme dizesi karşılaştırmaları, deyimin nasıl ayarlandığına bakılmaksızın büyük/küçük harfe duyarlıdır `Option Compare` .  
  
## <a name="dependent-_my-compilation-constants"></a>Bağımlı \_ derleme sabitlerim  

`_MYTYPE`Koşullu derleme sabiti, sırasıyla diğer birçok `_MY` derleme sabitlerinin değerlerini denetler:  
  
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
  
 Varsayılan olarak, tanımsız koşullu derleme sabitleri olarak çözümlenir `FALSE` . Varsayılan davranışı geçersiz kılmak için projenizi derlerken tanımsız sabitler için değerler belirtebilirsiniz.  
  
> [!NOTE]
> `_MYTYPE`"Custom" olarak ayarlandığında, proje `My` ad alanını içerir, ancak nesne içermez. Ancak, `_MYTYPE` "Empty" olarak ayarlandığında derleyicinin `My` ad alanını ve nesnelerini eklemesini önler.  
  
 Bu tabloda, derleme sabitlerinin önceden tanımlanmış değerlerinin etkileri açıklanmaktadır `_MY` .  
  
|Sabit|Anlamı|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|`My.Application`Sabit "konsol," Windows "veya" WindowsForms "ise, etkinleştirilir:<br /><br /> -"Konsol" sürümü öğesinden türetilir <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> . ve "Windows" sürümünden daha az üye içeriyor.<br />-"Windows" sürümü öğesinden türetilir <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> . ve "WindowsForms" sürümünden daha az üye içeriyor.<br />-"WindowsForms" sürümü `My.Application` öğesinden türetilir <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> . `TARGET`Sabit "winexe" olarak tanımlanmışsa, sınıf bir `Sub Main` yöntemi içerir.|  
|`_MYCOMPUTERTYPE`|`My.Computer`, Sabit "Web" veya "Windows" ise izin vermez:<br /><br /> -"Web" sürümü öğesinden türetilir <xref:Microsoft.VisualBasic.Devices.ServerComputer> ve "Windows" sürümünden daha az üyeye sahiptir.<br />-"Windows" sürümü, `My.Computer` öğesinden türetilir <xref:Microsoft.VisualBasic.Devices.Computer> .|  
|`_MYFORMS`|`My.Forms`Sabit ise, etkinleştirilir `TRUE` .|  
|`_MYUSERTYPE`|`My.User`, Sabit "Web" veya "Windows" ise izin vermez:<br /><br /> -"Web" sürümü `My.User` GEÇERLI http isteğinin kullanıcı kimliğiyle ilişkili.<br />-"Windows" sürümü, `My.User` iş parçacığının geçerli sorumlusu ile ilişkilendirilmiştir.|  
|`_MYWEBSERVICES`|`My.WebServices`Sabit ise, etkinleştirilir `TRUE` .|  
|`_MYTYPE`|, `My.Log` , `My.Request` Ve `My.Response` sabiti "Web" ise etkinleştirilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My Özellikleri Proje Türüne Nasıl Bağımlıdır](../development-with-my/how-my-depends-on-project-type.md)
- [Koşullu Derleme](../../programming-guide/program-structure/conditional-compilation.md)
- [-tanımla (Visual Basic)](../../reference/command-line-compiler/define.md)
- [My.Forms Nesnesi](../../language-reference/objects/my-forms-object.md)
- [My.Request Nesnesi](../../language-reference/objects/my-request-object.md)
- [My.Response Nesnesi](../../language-reference/objects/my-response-object.md)
- [My.WebServices Nesnesi](../../language-reference/objects/my-webservices-object.md)
