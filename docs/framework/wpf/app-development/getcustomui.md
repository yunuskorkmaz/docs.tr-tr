---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: a9c4c9d597f5cc1b172213d49a3dd5b8f1c1f671
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991373"
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
  
 dışı Konak tarafından sağlanan ilerleme Kullanıcı arabirimi olan sınıfın adı, tercihen içeren [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] <xref:System.Windows.Controls.Page> bir dosya en üst düzey öğesidir. Bu sınıf, tarafından `pwzProgressAssemblyName`belirtilen derlemede bulunur.  
  
 `pwzErrorAssemblyName`  
  
 dışı Konak tarafından sağlanan hata Kullanıcı arabirimini içeren derlemeye yönelik bir işaretçi.  
  
 `pwzErrorClassName`  
  
 dışı Konak tarafından sağlanan hata Kullanıcı arabirimi olan sınıfın adı, tercihen içeren <xref:System.Windows.Controls.Page> bir xaml dosyası, en üst düzey öğesidir. Bu sınıf, tarafından `pwzErrorAssemblyName`belirtilen derlemede bulunur.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT LIP.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ana bilgisayar uygulaması, PresentationHost. exe ' nin varsayılan kullanıcı arabirimlerinin uygun olabileceği belirli bir temaya sahip olabilir. Bu durumda, konak uygulama, PresentationHost. exe ' ye ilerleme ve hata kullanıcı arabirimlerini döndürmek için [GetCustomUI](getcustomui.md) uygulayabilir. PresentationHost. exe, varsayılan kullanıcı arabirimlerini kullanmadan önce her zaman [GetCustomUI](getcustomui.md) öğesini çağırır.  
  
 Bu işlev, PresentationHost 'ın başlatılması sırasında bir kez çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IWpfHostSupport](iwpfhostsupport.md)
