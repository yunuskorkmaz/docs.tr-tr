---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 91a29233d12a842a64b7d3dd497312f6dc6742ca
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423645"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
PresentationHost. exe aracılığıyla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içeriği barındıran uygulamalar, ana bilgisayar ve PresentationHost. exe arasında bir tümleştirme noktası sağlamak için bu arabirimi uygular.  
  
## <a name="remarks"></a>Açıklamalar  
 Web tarayıcıları gibi [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalar, XAML tarayıcı uygulamaları (XBAP) ve gevşek XAML dahil olmak üzere WPF içeriğini barındırabilir. [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalar, WPF içeriğini barındırmak için [WebBrowser denetiminin](https://go.microsoft.com/fwlink/?LinkId=97911)bir örneğini oluşturur. WPF, barındırılan bir PresentationHost. exe ' nin bir örneğini oluşturur ve bu, [WebBrowser denetiminde](https://go.microsoft.com/fwlink/?LinkId=97911)görüntülenmek üzere konak IÇIN barındırılan WPF içeriğini sağlar.  
  
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
|[FilterInputMessage](filterinputmessage.md)|E_NOTIMPL döndürülmediği müddetçe PresentationHost. exe tarafından çağırılır.|  
|[GetCustomUI](getcustomui.md)|Varsayılan olarak, PresentationHost. exe kendi dağıtım ilerlemesini ve WPF içeriği dağıtıldığında görüntülenen dağıtım hatası kullanıcı arabirimlerini sağlar.|
