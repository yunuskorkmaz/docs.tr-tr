---
title: My Özellikleri Proje Türüne Nasıl Bağımlıdır (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 989329da7dc57cd50b9ce6c88117152d0cb93d66
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775194"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>My Özellikleri Proje Türüne Nasıl Bağımlıdır (Visual Basic)
`My` yalnızca belirli bir proje türü için gereken nesneleri kullanıma sunar. Örneğin, `My.Forms` nesnesi bir Windows Forms uygulamasında kullanılabilir ancak konsol uygulamasında kullanılamaz. Bu konuda, farklı proje türlerinde hangi `My` nesnelerinin kullanılabildiği açıklanmaktadır.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>My Windows Uygulamaları ve Web siteleri  
 `My` yalnızca geçerli proje türünde yararlı olan nesneleri kullanıma sunar; geçerli olmayan nesneleri bastırır. Örneğin, aşağıdaki görüntüde `My` nesne modeli bir Windows Forms projesinde gösterilmektedir.  
  
 ![Windows Forms uygulamasındaki nesnem modelini gösteren diyagram.](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 Bir Web sitesi projesinde, ilgili olmayan nesneleri (`My.Forms` nesnesi gibi) gösterirken, bir Web geliştiricisi ile ilgili nesneleri (`My.Request` ve `My.Response` nesneleri gibi) kullanıma sunar `My`. Aşağıdaki görüntüde `My` nesne modeli bir Web sitesi projesinde gösterilmektedir:  
  
 ![Web uygulamasındaki nesnem modelini gösteren diyagram.](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>Proje ayrıntıları  
 Aşağıdaki tabloda sekiz proje türü için varsayılan olarak hangi `My` nesnelerinin etkinleştirildiği gösterilmektedir: Windows uygulaması, sınıf kitaplığı, konsol uygulaması, Windows Denetim Kitaplığı, Web denetim kitaplığı, Windows hizmeti, boş ve Web sitesi.  
  
 @No__t_0 nesnesinin üç sürümü, `My.Computer` nesnesinin iki sürümü ve `My.User` nesnesinin iki sürümü vardır. Bu sürümler hakkındaki ayrıntılar, tablodan sonraki dipnotlara göre verilmiştir.  
  
|Nesnem|Windows uygulaması|Sınıf Kitaplığı|Konsol Uygulaması|Windows Denetim Kitaplığı|Web Denetim Kitaplığı|Windows Hizmeti|Olmamalıdır|Web Sitesi|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Evet** <sup>1</sup>|**Evet** <sup>2</sup>|**Evet** <sup>3</sup>|**Evet** <sup>2</sup>|Hayır|**Evet** <sup>3</sup>|Hayır|Hayır|  
|`My.Computer`|**Evet** <sup>4</sup>|**Evet** <sup>4</sup>|**Evet** <sup>4</sup>|**Evet** <sup>4</sup>|**Evet** <sup>5</sup>|**Evet** <sup>4</sup>|Hayır|**Evet** <sup>5</sup>|  
|`My.Forms`|**Yes**|Hayır|Hayır|**Yes**|Hayır|Hayır|Hayır|Hayır|  
|`My.Log`|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|**Yes**|  
|`My.Request`|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|**Yes**|  
|`My.Resources`|**Yes**|**Yes**|**Yes**|**Yes**|**Yes**|**Yes**|Hayır|Hayır|  
|`My.Response`|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|**Yes**|  
|`My.Settings`|**Yes**|**Yes**|**Yes**|**Yes**|**Yes**|**Yes**|Hayır|Hayır|  
|`My.User`|**Evet** <sup>6</sup>|**Evet** <sup>6</sup>|**Evet** <sup>6</sup>|**Evet** <sup>6</sup>|**Evet** <sup>7</sup>|**Evet** <sup>6</sup>|Hayır|**Evet** <sup>7</sup>|  
|`My.WebServices`|**Yes**|**Yes**|**Yes**|**Yes**|**Yes**|**Yes**|Hayır|Hayır|  
  
 <sup>1</sup> Windows Forms `My.Application` sürümü. Konsol sürümünden türetilir (bkz. Note 3); uygulamanın pencereleri ile etkileşim kurma desteği ekler ve Visual Basic uygulama modeli sağlar.  
  
 `My.Application` <sup>2</sup> kitaplığı sürümü. Bir uygulama için gereken temel işlevselliği sağlar: uygulama günlüğüne yazmak ve uygulama bilgilerine erişmek için Üyeler sağlar.  
  
 `My.Application` <sup>3</sup> konsol sürümü. Kitaplık sürümünden türetilir (bkz. Note 2) ve uygulamanın komut satırı bağımsız değişkenlerine ve ClickOnce dağıtım bilgilerine erişmek için ek Üyeler ekler.  
  
 <sup>4</sup> `My.Computer` Windows sürümü. Sunucu sürümünden türetilir (bkz. Note 5) ve bir istemci makinesinde klavye, ekran ve fare gibi faydalı nesnelere erişim sağlar.  
  
 `My.Computer` <sup>5</sup> sunucu sürümü. Bilgisayar hakkında ad, saate erişim vb. gibi temel bilgileri sağlar.  
  
 `My.User` <sup>6</sup> Windows sürümü. Bu nesne, iş parçacığının geçerli kimliğiyle ilişkili.  
  
 `My.User` <sup>7</sup> Web sürümü. Bu nesne, uygulamanın geçerli HTTP isteğinin kullanıcı kimliğiyle ilişkili.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-tanımla (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response Nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
