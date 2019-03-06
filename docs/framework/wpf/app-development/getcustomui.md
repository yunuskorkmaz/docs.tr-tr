---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: 623ff5d14db6ae9cc5999aa184b81d6b22f4b201
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365015"
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
 Bir ana bilgisayar uygulaması PresentationHost.exe ait varsayılan kullanıcı arabirimleri için uymayabilir belirli bir tema olabilir. Bu durumda, ana bilgisayar uygulaması uygulayabilirsiniz [GetCustomUI](getcustomui.md) ilerleme durumu ve hata PresentationHost.exe için kullanıcı arabirimleri dönün. PresentationHost.exe her zaman çağıracaktır [GetCustomUI](getcustomui.md) varsayılan kullanıcı arabirimlerini kullanmadan önce.  
  
 Bu işlev, bir kez PresentationHost'un sırasında çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IWpfHostSupport](iwpfhostsupport.md)
