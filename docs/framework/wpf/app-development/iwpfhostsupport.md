---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 85309e46403b2f22f9afb760d4c4ae370c39246b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004095"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
PresentationHost. exe aracılığıyla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içeriğini barındıran uygulamalar, ana bilgisayar ve PresentationHost. exe arasında bir tümleştirme noktası sağlamak için bu arabirimi uygular.  
  
## <a name="remarks"></a>Açıklamalar  
 Web tarayıcıları gibi [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamaları, [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ve gevşek XAML dahil olmak üzere WPF içeriğini barındırabilirler. @No__t-0 uygulamaları, WPF içeriğini barındırmak için [WebBrowser denetiminin](https://go.microsoft.com/fwlink/?LinkId=97911)bir örneğini oluşturur. WPF, barındırılan bir PresentationHost. exe ' nin bir örneğini oluşturur ve bu, [WebBrowser denetiminde](https://go.microsoft.com/fwlink/?LinkId=97911)görüntülenmek üzere konak IÇIN barındırılan WPF içeriğini sağlar.  
  
 @No__t-0 tarafından etkinleştirilen tümleştirme PresentationHost. exe ' ye izin veriyor:  
  
- Ana bilgisayar uygulamasının ilgilendiği ham giriş cihazlarını (Insan arabirim aygıtları) bulun ve bunlarla kaydolun.  
  
- Kayıtlı ham giriş cihazlarından giriş iletileri alın ve uygun iletileri konak uygulamasına iletin.  
  
- Özel ilerleme ve hata Kullanıcı arabirimleri için konak uygulamasını sorgulayın.  
  
> [!NOTE]
> Bu API yalnızca yerel istemci makinesinde kullanılmak üzere tasarlanmıştır ve desteklenir  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|PresentationHost. exe ' nin, ana bilgisayar uygulamasının ilgilendiği ham giriş cihazlarını (Insan arabirimi cihazları) bulmasını sağlar.|  
|[FilterInputMessage](filterinputmessage.md)|E_NOTIMPL döndürülmediği müddetçe PresentationHost. exe tarafından çağırılır.|  
|[GetCustomUI](getcustomui.md)|Varsayılan olarak, PresentationHost. exe kendi dağıtım ilerlemesini ve WPF içeriği dağıtıldığında görüntülenen dağıtım hatası kullanıcı arabirimlerini sağlar.|
