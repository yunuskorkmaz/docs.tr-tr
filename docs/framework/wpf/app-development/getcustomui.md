---
title: GetCustomUI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 88c2873a5929e25335b0c6ef64f8121e31177ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getcustomui"></a>GetCustomUI
Ana bilgisayardan özel ilerleme durumu ve hata iletileri almak için PresentationHost.exe tarafından uygulanırsa çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwzProgressAssemblyName`  
  
 [out] Ana bilgisayar tarafından sağlanan kullanıcı arabirimi içeren bütünleştirilmiş kodun bir işaretçi.  
  
 `pwzProgressClassName`  
  
 [out] Ana bilgisayar tarafından sağlanan kullanıcı arabirimi, tercihen olduğu sınıfın adını bir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ile dosya <xref:System.Windows.Controls.Page> kendi üst seviye öğesidir. Bu sınıf tarafından belirtilen derleme bulunur `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 [out] Ana bilgisayar tarafından sağlanan hata kullanıcı arabirimi içeren bütünleştirilmiş kodun bir işaretçi.  
  
 `pwzErrorClassName`  
  
 [out] Ana bilgisayar tarafından sağlanan hata kullanıcı sınıfının arabirim adı, tercihen ile bir XAML dosyası <xref:System.Windows.Controls.Page> kendi üst seviye öğesidir. Bu sınıf tarafından belirtilen derleme bulunur `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT: yoksayıldı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ana bilgisayar uygulaması PresentationHost.exe'nin varsayılan kullanıcı arabirimleri için uygun olmayabilir belirli bir temaya sahip olabilir. Bu durumda, ana bilgisayar uygulamasını uygulayabilirsiniz [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) ilerleme durumu ve hata kullanıcı arabirimleri PresentationHost.exe'ye izin verilecek. PresentationHost.exe her zaman çağıracaktır [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) varsayılan kullanıcı arabirimlerinden kullanmadan önce.  
  
 Bu işlev bir kez PresentationHost'un sırasında çağrılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IWpfHostSupport](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)
