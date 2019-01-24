---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: 012590a21ac24b1146c30405c9872355a4b50802
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627258"
---
# <a name="getcustomui"></a>GetCustomUI
Konaktan özel ilerleme durumu ve hata iletileri almak için PresentationHost.exe tarafından uygulanması durumunda çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwzProgressAssemblyName`  
  
 [out] Ana bilgisayar tarafından sağlanan kullanıcı arabirimi içeren derleme için bir işaretçi.  
  
 `pwzProgressClassName`  
  
 [out] Ana bilgisayar tarafından sağlanan kullanıcı arabirimi, tercihen olduğu sınıfın adını bir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ile dosya <xref:System.Windows.Controls.Page> kendi üst düzey bir öğedir. Bu sınıf tarafından belirtilen derlemede bulunan `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 [out] Ana bilgisayar tarafından sağlanan hata kullanıcı arabirimi içeren derleme için bir işaretçi.  
  
 `pwzErrorClassName`  
  
 [out] Ana bilgisayar tarafından sağlanan hata kullanıcı sınıf adı arabirim, tercihen bir XAML dosyasıyla <xref:System.Windows.Controls.Page> kendi üst düzey bir öğedir. Bu sınıf tarafından belirtilen derlemede bulunan `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT: Yoksayıldı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ana bilgisayar uygulaması PresentationHost.exe ait varsayılan kullanıcı arabirimleri için uymayabilir belirli bir tema olabilir. Bu durumda, ana bilgisayar uygulaması uygulayabilirsiniz [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) ilerleme durumu ve hata PresentationHost.exe için kullanıcı arabirimleri dönün. PresentationHost.exe her zaman çağıracaktır [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) varsayılan kullanıcı arabirimlerini kullanmadan önce.  
  
 Bu işlev, bir kez PresentationHost'un sırasında çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IWpfHostSupport](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)
