---
title: COM Birlikte Çalışması Özel Durumlarını İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: 42efd1a5622bae7c476c92fb0864a6214c9bac9b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726190"
---
# <a name="handling-com-interop-exceptions"></a>COM Birlikte Çalışması Özel Durumlarını İşleme

Yönetilen ve yönetilmeyen kod, özel durumları işlemek için birlikte çalışabilir. Bir yöntem yönetilen kodda bir özel durum oluşturursa, ortak dil çalışma zamanı bir HRESULT 'yi bir COM nesnesine geçirebilir. Bir yöntem HRESULT hatası döndürerek yönetilmeyen kodda başarısız olursa, çalışma zamanı yönetilen kod tarafından yakalanamayan bir özel durum oluşturur.  
  
 Çalışma zamanı, HRESULT 'yi COM birlikte çalışabilirliğine özel özel durumlarla otomatik olarak eşleştirir. Örneğin, E_ACCESSDENIED olur, <xref:System.UnauthorizedAccessException> e_outofmemory olur <xref:System.OutOfMemoryException> ve bu şekilde devam eder.  
  
 HRESULT özel bir sonuçse veya çalışma zamanı için bilinmiyorsa, çalışma zamanı istemciye genel geçirir <xref:System.Runtime.InteropServices.COMException> . **COMException** öğesinin **ErrorCode** özelliği HRESULT değerini içerir.  
  
## <a name="working-with-ierrorinfo"></a>IErrorInfo ile çalışma  

 COM 'dan yönetilen koda bir hata geçirildiğinde, çalışma zamanı özel durum nesnesini hata bilgileriyle doldurur. IErrorInfo ve döndürülen HRESULTS 'leri destekleyen COM nesneleri, bu bilgileri yönetilen kod özel durumlarına sağlar. Örneğin, çalışma zamanı, açıklamayı COM hatasından özel durumun <xref:System.Exception.Message%2A> özelliğine eşler. HRESULT ek bir hata bilgisi sunduğunda, çalışma zamanı özel durum özelliklerinin çoğunu varsayılan değerlerle doldurur.  
  
 Yönetilmeyen kodda bir yöntem başarısız olursa, yönetilen bir kod kesimine özel durum geçirilebilir. [HResults ve Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) konuları, HResults 'ın çalışma zamanı özel durum nesneleriyle nasıl eşlendiğini gösteren bir tablo içerir.  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
