---
title: My Özellikleri Proje Türüne Nasıl Bağımlıdır (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 72b9799d1f5ba7efa37d5f8f2a633e6806a58607
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63808086"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>My Özellikleri Proje Türüne Nasıl Bağımlıdır (Visual Basic)
`My` yalnızca belirli proje türü tarafından gerekli nesneleri gösterir. Örneğin, `My.Forms` nesnesi olan bir Windows Forms uygulamasında kullanılabilir, ancak bir konsol uygulaması kullanılabilir değil. Bu konuda açıklayan `My` nesneleri farklı proje türlerinde kullanılabilir.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>My içinde Windows uygulamaları ve Web siteleri  
 `My` Geçerli proje türünde yararlı olan nesneleri gösterir; Bu, geçerli olmayan nesneler bastırır. Örneğin, aşağıdaki gösterir görüntüde `My` nesne modelinde bir Windows Forms projesi.  
  
 ![Gösteren diyagram My nesne modelinde bir Windows Forms uygulaması.](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 Bir Web sitesi projesindeki `My` bir Web geliştiricisi için uygun olan nesneler sunar (gibi `My.Request` ve `My.Response` nesneleri) ilgili olmayan nesneler gizleme sırasında (gibi `My.Forms` nesne). Aşağıdaki görüntüde `My` nesne modelinde bir Web sitesi projesi:  
  
 ![Gösteren diyagram My nesne modeli bir Web uygulaması.](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>Proje Ayrıntıları  
 Aşağıdaki tabloda gösterir `My` nesneleri, varsayılan olarak etkinleştirilir, sekiz proje türleri için: Windows uygulama, sınıf kitaplığı, konsol uygulaması, Windows Denetim Kitaplığı, Web denetim kitaplığı, Windows hizmeti, boş ve Web sitesi.  
  
 Üç sürümü vardır `My.Application` nesnesi, iki sürümünü `My.Computer` nesne ve iki sürümünü `My.User` nesne; bu sürümler hakkında ayrıntılar içinde dipnotlar tablodan sonra verilmiştir.  
  
|Nesnem|Windows uygulama|Sınıf Kitaplığı|Konsol Uygulaması|Windows Denetim Kitaplığı|Web Denetim Kitaplığı|Windows Hizmeti|boş|Web Sitesi|  
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
  
 <sup>1</sup> Windows Forms sürümünü `My.Application`. Konsol sürümünden türetilen (bkz. Not 3); uygulamanın windows ile etkileşim kurmak için destek ekler ve Visual Basic uygulama modeli sağlar.  
  
 <sup>2</sup> kitaplık sürümünü `My.Application`. Bir uygulama için gerekli temel işlevleri sağlar: uygulama bilgilerine erişmek ve uygulama günlüğüne yazmak için üyeleri sağlar.  
  
 <sup>3</sup> konsol sürümü `My.Application`. Kitaplık sürümünden türetilen (bkz. Not 2), ve uygulamanın komut satırı bağımsız değişkenleri ve ClickOnce dağıtım bilgilerini erişmek için ek üyeler ekler.  
  
 <sup>4</sup> Windows sürümünü `My.Computer`. Türetilen sunucu sürümünden (bkz. Not 5) ve klavye, ekran ve fare gibi bir istemci makine üzerinde kullanışlı nesnelere erişim sağlar.  
  
 <sup>5</sup> sunucu sürümünü `My.Computer`. Bilgisayarın adı, saati ve benzeri erişim gibi ilgili temel bilgileri sağlar.  
  
 <sup>6</sup> Windows sürümünü `My.User`. Bu nesne, geçerli iş parçacığının kimliği ile ilişkilidir.  
  
 <sup>7</sup> web sürümünü `My.User`. Bu nesne, uygulamanın geçerli HTTP isteği kullanıcı kimliğiyle ilişkilendirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response Nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
