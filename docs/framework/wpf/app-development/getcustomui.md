---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: e9ef32912c2afb3c99e46e1e14bb3daa5a2e99af
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005716"
---
# <a name="getcustomui"></a>GetCustomUI
Uygulanırsa, konaktan Özel ilerleme ve hata iletilerini almak için PresentationHost. exe tarafından çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzProgressAssemblyName`  
  
 dışı Konak tarafından sağlanan ilerleme Kullanıcı arabirimini içeren derlemeye yönelik bir işaretçi.  
  
 `pwzProgressClassName`  
  
 dışı Konak tarafından sağlanan ilerleme Kullanıcı arabirimi olan sınıfın adı, tercihen <xref:System.Windows.Controls.Page> olan XAML dosyası en üst düzey öğesidir. Bu sınıf `pwzProgressAssemblyName` tarafından belirtilen derlemede bulunur.  
  
 `pwzErrorAssemblyName`  
  
 dışı Konak tarafından sağlanan hata Kullanıcı arabirimini içeren derlemeye yönelik bir işaretçi.  
  
 `pwzErrorClassName`  
  
 dışı Konak tarafından sağlanan hata Kullanıcı arabirimi olan sınıfın adı, tercihen <xref:System.Windows.Controls.Page> olan XAML dosyası en üst düzey öğesidir. Bu sınıf `pwzErrorAssemblyName` tarafından belirtilen derlemede bulunur.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT: yoksayıldı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ana bilgisayar uygulaması, PresentationHost. exe ' nin varsayılan kullanıcı arabirimlerinin uygun olabileceği belirli bir temaya sahip olabilir. Bu durumda, konak uygulama, PresentationHost. exe ' ye ilerleme ve hata kullanıcı arabirimlerini döndürmek için [GetCustomUI](getcustomui.md) uygulayabilir. PresentationHost. exe, varsayılan kullanıcı arabirimlerini kullanmadan önce her zaman [GetCustomUI](getcustomui.md) öğesini çağırır.  
  
 Bu işlev, PresentationHost 'ın başlatılması sırasında bir kez çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IWpfHostSupport](iwpfhostsupport.md)
