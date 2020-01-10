---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 4855fae2954e5650d8c9bbb81153ebe64249a867
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740184"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
PresentationHost. exe aracılığıyla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içeriği barındıran uygulamalar, ana bilgisayar ve PresentationHost. exe arasında bir tümleştirme noktası sağlamak için bu arabirimi uygular.  
  
## <a name="remarks"></a>Açıklamalar  
 Web tarayıcıları gibi Win32 uygulamaları, XAML tarayıcı uygulamaları (XBAP 'ler) ve gevşek XAML dahil olmak üzere WPF içeriği barındıralabilir. WPF içeriğini barındırmak için, Win32 uygulamaları [WebBrowser denetiminin](https://go.microsoft.com/fwlink/?LinkId=97911)bir örneğini oluşturur. WPF, barındırılan bir PresentationHost. exe ' nin bir örneğini oluşturur ve bu, [WebBrowser denetiminde](https://go.microsoft.com/fwlink/?LinkId=97911)görüntülenmek üzere konak IÇIN barındırılan WPF içeriğini sağlar.  
  
 `IWpfHostSupport` tarafından etkinleştirilen tümleştirme PresentationHost. exe ' ye izin veriyor:  
  
- Ana bilgisayar uygulamasının ilgilendiği ham giriş cihazlarını (Insan arabirim aygıtları) bulun ve bunlarla kaydolun.  
  
- Kayıtlı ham giriş cihazlarından giriş iletileri alın ve uygun iletileri konak uygulamasına iletin.  
  
- Özel ilerleme ve hata Kullanıcı arabirimleri için konak uygulamasını sorgulayın.  
  
> [!NOTE]
> Bu API yalnızca yerel istemci makinesinde kullanılmak üzere tasarlanmıştır ve desteklenir  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|PresentationHost. exe ' nin, ana bilgisayar uygulamasının ilgilendiği ham giriş cihazlarını (Insan arabirimi cihazları) bulmasını sağlar.|  
|[FilterInputMessage](filterinputmessage.md)|E_NOTIMPL döndürülmediği takdirde PresentationHost. exe tarafından çağırılır.|  
|[GetCustomUI](getcustomui.md)|Varsayılan olarak, PresentationHost. exe kendi dağıtım ilerlemesini ve WPF içeriği dağıtıldığında görüntülenen dağıtım hatası kullanıcı arabirimlerini sağlar.|
