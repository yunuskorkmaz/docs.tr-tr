---
title: IWpfHostSupport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 85d4ed09d6c5ca17e148d531e6aac483ff737d51
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Ana bilgisayar uygulamaları [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] PresentationHost.exe üzerinden içerik PresentationHost.exe ve ana bilgisayar arasında tümleştirme noktası sağlamak için bu arabirimi uygulayan.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]Web tarayıcıları gibi uygulamaları barındırabilir [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] dahil olmak üzere içerik [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ve XAML kaybedilir. Ana bilgisayara [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] içerik [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamaları oluşturma örneği [WebBrowser denetimi](http://go.microsoft.com/fwlink/?LinkId=97911). Barındırılacak şekilde [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] barındırılan sağlar PresentationHost.exe örneği oluşturur [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] görüntülenmek üzere ana içerik [WebBrowser denetimi](http://go.microsoft.com/fwlink/?LinkId=97911).  
  
 Tarafından etkinleştirilen tümleştirme `IWpfHostSupport` PresentationHost.exe'ye izin verir:  
  
-   Bul ve ana uygulamanın ilgilendiği ham giriş aygıtlarını (İnsan Arabirimi aygıtları) ile kaydedin.  
  
-   Giriş kayıtlı ham giriş aygıtlarını ve uygun iletileri yönlendirmek için konak uygulama iletilerini.  
  
-   Özel ilerleme durumu ve hata kullanıcı arabirimleri için ana bilgisayar uygulaması sorgu.  
  
> [!NOTE]
>  Bu API yalnızca hedeflenen ve yerel istemci makinesinde kullanımı desteklenen  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|Ana uygulamanın ilgilendiği ham giriş aygıtlarını (İnsan Arabirimi aygıtları) keşfetmek için PresentationHost.exe'ye izin verir.|  
|[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|E_NOTIMPL sürece bir ileti alındığında PresentationHost.exe tarafından çağrılır.|  
|[GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)|Varsayılan olarak, PresentationHost.exe kendi dağıtımının ilerleme durumunu ve dağıtım hatası WPF içeriği dağıtıldığında görüntülenen kullanıcı arabirimleri sağlar.|
