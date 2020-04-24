---
title: My Özellikleri Proje Türüne Nasıl Bağımlıdır
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 975b8feb001bcab22185be0a360b0512de099b79
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330276"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>My Özellikleri Proje Türüne Nasıl Bağımlıdır (Visual Basic)

`My`yalnızca belirli bir proje türü için gereken nesneleri gösterir. Örneğin, `My.Forms` nesne Windows Forms bir uygulamada kullanılabilir ancak konsol uygulamasında kullanılamaz. Bu konuda, farklı `My` proje türlerinde hangi nesnelerin kullanılabildiği açıklanmaktadır.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>My Windows Uygulamaları ve Web siteleri  

 `My`yalnızca geçerli proje türünde yararlı olan nesneleri gösterir; geçerli olmayan nesneleri bastırır. Örneğin, aşağıdaki görüntüde `My` nesne modeli Windows Forms bir projede gösterilmektedir.  
  
 ![Windows Forms uygulamasındaki nesnem modelini gösteren diyagram.](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 `My` Bir Web sitesi projesinde, ilgili olmayan nesneleri (örneğin, `My.Request` `My.Response` `My.Forms` nesne) bastırırken bir Web geliştiricisi (ve nesneleri gibi) ile ilgili nesneleri ortaya koyar. Aşağıdaki görüntüde `My` nesne modeli bir Web sitesi projesinde gösterilmektedir:  
  
 ![Web uygulamasındaki nesnem modelini gösteren diyagram.](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>Proje ayrıntıları  

 Aşağıdaki tabloda sekiz proje türü `My` için varsayılan olarak etkinleştirilen nesneler gösterilmektedir: Windows uygulaması, sınıf kitaplığı, konsol uygulaması, Windows Denetim Kitaplığı, Web denetim kitaplığı, Windows hizmeti, boş ve Web sitesi.  
  
 `My.Application` Nesnenin üç sürümü, `My.Computer` nesnesinin iki sürümü ve iki `My.User` nesne sürümü vardır; Bu sürümler hakkındaki ayrıntılar, tablodan sonraki dipnotlara göre verilmiştir.  
  
|Nesnem|Windows uygulaması|Sınıf Kitaplığı|Konsol Uygulaması|Windows Denetim Kitaplığı|Web Denetim Kitaplığı|Windows Hizmeti|Olmamalıdır|Web Sitesi|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Evet** <sup>1</sup>|**Evet** <sup>2</sup>|**Evet** <sup>3</sup>|**Evet** <sup>2</sup>|Hayır|**Evet** <sup>3</sup>|Hayır|Hayır|  
|`My.Computer`|**Evet** <sup>4</sup>|**Evet** <sup>4</sup>|**Evet** <sup>4</sup>|**Evet** <sup>4</sup>|**Evet** <sup>5</sup>|**Evet** <sup>4</sup>|Hayır|**Evet** <sup>5</sup>|  
|`My.Forms`|**Evet**|Hayır|Hayır|**Evet**|Hayır|Hayır|Hayır|Hayır|  
|`My.Log`|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|**Evet**|  
|`My.Request`|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|**Evet**|  
|`My.Resources`|**Evet**|**Evet**|**Evet**|**Evet**|**Evet**|**Evet**|Hayır|Hayır|  
|`My.Response`|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|**Evet**|  
|`My.Settings`|**Evet**|**Evet**|**Evet**|**Evet**|**Evet**|**Evet**|Hayır|Hayır|  
|`My.User`|**Evet** <sup>6</sup>|**Evet** <sup>6</sup>|**Evet** <sup>6</sup>|**Evet** <sup>6</sup>|**Evet** <sup>7</sup>|**Evet** <sup>6</sup>|Hayır|**Evet** <sup>7</sup>|  
|`My.WebServices`|**Evet**|**Evet**|**Evet**|**Evet**|**Evet**|**Evet**|Hayır|Hayır|  
  
 <sup>1</sup> Windows Forms sürümü `My.Application`. Konsol sürümünden türetilir (bkz. Note 3); uygulamanın pencereleri ile etkileşim kurma desteği ekler ve Visual Basic uygulama modeli sağlar.  
  
 <sup>2</sup> kitaplık sürümü `My.Application`. Bir uygulama için gereken temel işlevselliği sağlar: uygulama günlüğüne yazmak ve uygulama bilgilerine erişmek için Üyeler sağlar.  
  
 <sup>3</sup> konsol sürümü `My.Application`. Kitaplık sürümünden türetilir (bkz. Note 2) ve uygulamanın komut satırı bağımsız değişkenlerine ve ClickOnce dağıtım bilgilerine erişmek için ek Üyeler ekler.  
  
 <sup>4</sup> Windows sürümü `My.Computer`. Sunucu sürümünden türetilir (bkz. Note 5) ve bir istemci makinesinde klavye, ekran ve fare gibi faydalı nesnelere erişim sağlar.  
  
 <sup>5</sup> sunucu sürümü `My.Computer`. Bilgisayar hakkında ad, saate erişim vb. gibi temel bilgileri sağlar.  
  
 <sup>6</sup> uygulamasının `My.User`6 Windows sürümü. Bu nesne, iş parçacığının geçerli kimliğiyle ilişkili.  
  
 <sup>'</sup> nin `My.User`7 Web sürümü. Bu nesne, uygulamanın geçerli HTTP isteğinin kullanıcı kimliğiyle ilişkili.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-tanımla (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response Nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
