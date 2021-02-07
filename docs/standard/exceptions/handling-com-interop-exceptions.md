---
description: 'Daha fazla bilgi edinin: COM birlikte çalışma özel durumlarını Işleme'
title: COM Birlikte Çalışması Özel Durumlarını İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: c7746f84d30dafcaf30c3d89d4319ca3fb2107d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713292"
---
# <a name="handling-com-interop-exceptions"></a>COM Birlikte Çalışması Özel Durumlarını İşleme

Yönetilen ve yönetilmeyen kod, özel durumları işlemek için birlikte çalışabilir. Bir yöntem yönetilen kodda bir özel durum oluşturursa, ortak dil çalışma zamanı bir HRESULT 'yi bir COM nesnesine geçirebilir. Bir yöntem HRESULT hatası döndürerek yönetilmeyen kodda başarısız olursa, çalışma zamanı yönetilen kod tarafından yakalanamayan bir özel durum oluşturur.  
  
 Çalışma zamanı, HRESULT 'yi COM birlikte çalışabilirliğine özel özel durumlarla otomatik olarak eşleştirir. Örneğin, E_ACCESSDENIED olur, <xref:System.UnauthorizedAccessException> e_outofmemory olur <xref:System.OutOfMemoryException> ve bu şekilde devam eder.  
  
 HRESULT özel bir sonuçse veya çalışma zamanı için bilinmiyorsa, çalışma zamanı istemciye genel geçirir <xref:System.Runtime.InteropServices.COMException> . **COMException** öğesinin **ErrorCode** özelliği HRESULT değerini içerir.  
  
## <a name="working-with-ierrorinfo"></a>IErrorInfo ile çalışma  

 COM 'dan yönetilen koda bir hata geçirildiğinde, çalışma zamanı özel durum nesnesini hata bilgileriyle doldurur. IErrorInfo ve döndürülen HRESULTS 'leri destekleyen COM nesneleri, bu bilgileri yönetilen kod özel durumlarına sağlar. Örneğin, çalışma zamanı, açıklamayı COM hatasından özel durumun <xref:System.Exception.Message%2A> özelliğine eşler. HRESULT ek bir hata bilgisi sunduğunda, çalışma zamanı özel durum özelliklerinin çoğunu varsayılan değerlerle doldurur.  
  
 Yönetilmeyen kodda bir yöntem başarısız olursa, yönetilen bir kod kesimine özel durum geçirilebilir. [HResults ve Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) konuları, HResults 'ın çalışma zamanı özel durum nesneleriyle nasıl eşlendiğini gösteren bir tablo içerir.  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
