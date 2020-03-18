---
title: COM Birlikte Çalışması Özel Durumlarını İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: 17cd739ac40b43bdd4a93b83a4ab9d0d92400e2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708938"
---
# <a name="handling-com-interop-exceptions"></a>COM Birlikte Çalışması Özel Durumlarını İşleme
Yönetilen ve yönetilmeyen kod, özel durumları işlemek için birlikte çalışabilir. Yönetilen kodda bir yöntem özel durum atarsa, ortak dil çalışma süresi bir Com nesnesine Bir HRESULT geçirebilir. Bir yöntem bir hata HRESULT döndürerek yönetilmeyen kod başarısız olursa, çalışma zamanı yönetilen kod tarafından yakalanmış olabilir bir özel durum atar.  
  
 Çalışma süresi otomatik olarak COM interop gelen HRESULT daha özel özel durumlar alakadar eşler. Örneğin, E_ACCESSDENIED <xref:System.UnauthorizedAccessException>olur , <xref:System.OutOfMemoryException>E_OUTOFMEMORY olur , ve benzeri.  
  
 HRESULT özel bir sonuçsa veya çalışma zamanı bilinmiyorsa, çalışma <xref:System.Runtime.InteropServices.COMException> süresi genel bir istemciye geçer. **COMException'ın** **ErrorCode** özelliği HRESULT değerini içerir.  
  
## <a name="working-with-ierrorinfo"></a>iErrorInfo ile çalışma  
 Com'dan yönetilen koda bir hata aktarıldığında, çalışma zamanı hata bilgileriyle özel durum nesnesini doldurur. IErrorInfo'u destekleyen ve HRESULTS'i döndüren COM nesneleri bu bilgileri yönetilen kod özel durumlarına sağlar. Örneğin, çalışma zamanı, Com hatasından özel <xref:System.Exception.Message%2A> durum özelliğine Açıklama eşler. HRESULT ek hata bilgisi sağlamazsa, çalışma süresi özel durum özelliklerinin çoğunu varsayılan değerlerle doldurur.  
  
 Bir yöntem yönetilmeyen kodda başarısız olursa, yönetilen kod kesimine bir özel durum geçirilebilir. Konu [HRESULTS ve Özel Durumlar](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) çalışma zamanı özel durum nesneleri için HRESULTS eşler nasıl gösteren bir tablo içerir.  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
