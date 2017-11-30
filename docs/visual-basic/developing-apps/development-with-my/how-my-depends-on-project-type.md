---
title: "My Özellikleri Proje Türüne Nasıl Bağımlıdır (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a37bf43096931597278974099becb9be6ae133d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>My Özellikleri Proje Türüne Nasıl Bağımlıdır (Visual Basic)
`My`yalnızca belirli proje türüne göre gereken nesneleri gösterir. Örneğin, `My.Forms` nesnesi olan bir Windows Forms uygulamasında kullanılabilir, ancak bir konsol uygulamasında mevcut değil. Bu konuda açıklayan `My` nesneleri farklı proje türlerinde kullanılabilir.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>İçinde Windows uygulamaları ve Web siteleri  
 `My`Geçerli proje türü yararlı olan nesneleri gösterir; geçerli olmayan nesneler gizler. Örneğin, aşağıdaki gösterir görüntü `My` nesne modelinde bir Windows Forms projesi.  
  
 ![Şeklin My bir Windows Forms uygulamasında](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 Bir Web sitesi projesindeki `My` Web geliştiricileri ile ilgili nesneler sunar (gibi `My.Request` ve `My.Response` nesneler) ilgili olmayan nesneler gizleme sırasında (gibi `My.Forms` nesnesi). Aşağıdaki resimde gösterildiği `My` bir Web sitesi projesini nesne modelinde:  
  
 ![Şeklin My bir Web uygulaması](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>Proje Ayrıntıları  
 Aşağıdaki tabloda gösterir `My` nesneleri, varsayılan olarak etkinleştirilir, sekiz türleri proje için: Windows uygulama, sınıf kitaplığı, konsol uygulaması, Windows Denetim Kitaplığı, Web kontrol kitaplığı, Windows hizmeti, boş ve Web sitesi.  
  
 Üç sürümü vardır `My.Application` nesnesi, iki sürümü `My.Computer` nesne ve iki sürümü `My.User` nesne; bu sürümleri ayrıntılarını tablodan sonra footnotes verilmiştir.  
  
|Nesnem|Windows uygulaması|Sınıf Kitaplığı|Konsol Uygulaması|Windows Denetim Kitaplığı|Web Denetim Kitaplığı|Windows Hizmeti|boş|Web Sitesi|  
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
  
 <sup>1</sup> Windows Forms sürümü `My.Application`. Konsol sürümünden türetilen (bkz. Not 3); uygulamanın windows ile etkileşim için destek ekler ve sağlar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] uygulama modeli.  
  
 <sup>2</sup> kitaplık sürümünü `My.Application`. Bir uygulama tarafından gerek duyulan temel işlevleri sağlar: uygulama günlüğüne yazma ve uygulama bilgilerine erişmek için üyeleri sağlar.  
  
 <sup>3</sup> konsol sürümü `My.Application`. Kitaplık sürümünden türetilen (bkz. Not 2), ve uygulamanın komut satırı bağımsız değişkenleri ve ClickOnce dağıtım bilgileri erişmek için ek üyeleri ekler.  
  
 <sup>4</sup> Windows sürümünü `My.Computer`. Sunucu sürümünden türetilen (bkz. Not 5) ve klavye, ekran ve fare gibi bir istemci makine üzerinde yararlı nesnelere erişim sağlar.  
  
 <sup>5</sup> sunucu sürümü `My.Computer`. Bilgisayar adı, saati ve benzeri erişim gibi hakkında temel bilgiler sağlar.  
  
 <sup>6</sup> Windows sürümünü `My.User`. Bu nesne iş parçacığının geçerli kimliği ile ilişkilidir.  
  
 <sup>7</sup> web sürümü `My.User`. Bu uygulamanın geçerli HTTP isteği kullanıcı kimliğiyle ilişkili nesnesidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Özelleştirme hangi nesnelerin kullanılabilir olduğunu My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [My.Forms nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.Request nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [My.Response nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [My.WebServices nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
