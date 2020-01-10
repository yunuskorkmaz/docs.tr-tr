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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708938"
---
# <a name="handling-com-interop-exceptions"></a>COM Birlikte Çalışması Özel Durumlarını İşleme
Yönetilen ve yönetilmeyen kod, özel durumları işlemek için birlikte çalışabilir. Bir yöntem yönetilen kodda bir özel durum oluşturursa, ortak dil çalışma zamanı bir HRESULT 'yi bir COM nesnesine geçirebilir. Bir yöntem HRESULT hatası döndürerek yönetilmeyen kodda başarısız olursa, çalışma zamanı yönetilen kod tarafından yakalanamayan bir özel durum oluşturur.  
  
 Çalışma zamanı, HRESULT 'yi COM birlikte çalışabilirliğine özel özel durumlarla otomatik olarak eşleştirir. Örneğin, E_ACCESSDENIED <xref:System.UnauthorizedAccessException>olur E_OUTOFMEMORY <xref:System.OutOfMemoryException>olur.  
  
 HRESULT özel bir sonuçse veya çalışma zamanı için bilinmiyorsa, çalışma zamanı istemciye genel <xref:System.Runtime.InteropServices.COMException> geçirir. **COMException** öğesinin **ErrorCode** özelliği HRESULT değerini içerir.  
  
## <a name="working-with-ierrorinfo"></a>IErrorInfo ile çalışma  
 COM 'dan yönetilen koda bir hata geçirildiğinde, çalışma zamanı özel durum nesnesini hata bilgileriyle doldurur. IErrorInfo ve döndürülen HRESULTS 'leri destekleyen COM nesneleri, bu bilgileri yönetilen kod özel durumlarına sağlar. Örneğin, çalışma zamanı, açıklamayı COM hatasından özel durumun <xref:System.Exception.Message%2A> özelliğine eşler. HRESULT ek bir hata bilgisi sunduğunda, çalışma zamanı özel durum özelliklerinin çoğunu varsayılan değerlerle doldurur.  
  
 Yönetilmeyen kodda bir yöntem başarısız olursa, yönetilen bir kod kesimine özel durum geçirilebilir. [HResults ve Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) konuları, HResults 'ın çalışma zamanı özel durum nesneleriyle nasıl eşlendiğini gösteren bir tablo içerir.  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
