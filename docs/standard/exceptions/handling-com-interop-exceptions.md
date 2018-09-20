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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a17752257589ea4ee4d9e58182d4448f02f6460
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323132"
---
# <a name="handling-com-interop-exceptions"></a>COM Birlikte Çalışması Özel Durumlarını İşleme
Yönetilen ve yönetilmeyen kod özel durumları işlemek için birlikte çalışabilir. Bir yöntem, yönetilen kodda bir özel durum oluşturursa, ortak dil çalışma zamanı için bir COM nesnesi HRESULT geçirebilirsiniz. Bir hata HRESULT döndüren bir yöntemi yönetilmeyen kodda başarısız olursa, çalışma zamanı, yönetilen kod tarafından yakalanan özel durum oluşturur.  
  
 Çalışma zamanı, COM birlikte çalışma HRESULT daha ayrıntılı özel durumlar için otomatik olarak eşler. Örneğin, E_ACCESSDENIED olur <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY olur <xref:System.OutOfMemoryException>ve benzeri.  
  
 HRESULT özel bir sonuç ise veya çalışma zamanı bilinmiyorsa, genel çalışma geçirir <xref:System.Runtime.InteropServices.COMException> istemciye. **ErrorCode** özelliği **COMException** HRESULT değerini içerir.  
  
## <a name="working-with-ierrorinfo"></a>IErrorInfo ile çalışma  
 Yönetilen kod için hata COM'dan geçirildiğinde, çalışma zamanı hata bilgilerini özel durum nesnesiyle doldurur. IErrorInfo destekleyen ve HRESULTS dönüş COM nesneleri, yönetilen kod özel durumlar için bu bilgileri sağlayın. Örneğin, çalışma zamanı özel durumun COM hata açıklamasını eşler <xref:System.Exception.Message%2A> özelliği. HRESULT ek hata bilgisi sağlıyorsa, çalışma zamanının birçok özel durumun özellikleri varsayılan değerlerle doldurur.  
  
 Yönetilmeyen kodda bir yöntem başarısız olursa, bir özel durum için bir yönetilen kod kesimi geçirilebilir. Konu [HRESULTS ve özel durumları](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) HRESULTS çalışma zamanı özel durum nesnelere nasıl eşleştiğini gösteren bir tablo içeriyor.  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
