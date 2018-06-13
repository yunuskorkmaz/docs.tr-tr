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
ms.openlocfilehash: 9f4429d50f6b7646cb75fad44957a98812282928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571270"
---
# <a name="handling-com-interop-exceptions"></a>COM Birlikte Çalışması Özel Durumlarını İşleme
Yönetilen ve yönetilmeyen kod birlikte özel durumları işleme çalışabilirsiniz. Bir yöntem yönetilen kodda bir özel durum oluşturursa, ortak dil çalışma zamanı için bir COM nesnesi HRESULT geçirebilirsiniz. HRESULT hata döndürerek yönetilmeyen kodunda bir yöntem başarısız olursa, çalışma zamanı tarafından yönetilen kod görevinde bir özel durum oluşturur.  
  
 Çalışma zamanı COM birlikte çalışma HRESULT ayrıntılı özel durumlar otomatik olarak eşlenir. Örneğin, E_ACCESSDENIED hale <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY hale <xref:System.OutOfMemoryException>ve benzeri.  
  
 Özel bir sonuç HRESULT ise veya çalışma zamanına bilinmiyorsa, çalışma zamanı genel geçirir <xref:System.Runtime.InteropServices.COMException> istemciye. **ErrorCode** özelliği **COMException** HRESULT değeri içerir.  
  
## <a name="working-with-ierrorinfo"></a>IErrorInfo ile çalışma  
 Bir hata, yönetilen kod için COM geçirildiğinde, çalışma zamanı özel durum nesnesi hata bilgilerle doldurur. IErrorInfo destekleyen ve HRESULTS dönüş COM nesneleri yönetilen kod özel durumlar için bu bilgileri sağlar. Örneğin, çalışma zamanı özel durumun COM hatadan açıklamayı eşlemeleri <xref:System.Exception.Message%2A> özelliği. HRESULT ek hata bilgisi sağlarsa, çalışma zamanı birçok özel durumun özellikleri varsayılan değerlerle doldurur.  
  
 Yönetilmeyen kod içinde bir yöntem başarısız olursa, bir özel durum bir yönetilen kod kesimi geçirilebilir. Konu [HRESULTS ve özel durumları](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) nasıl HRESULTS çalışma zamanı özel durum nesnelere eşleme gösteren bir tablo içeriyor.  

## <a name="see-also"></a>Ayrıca Bkz.
[Özel Durumlar](index.md) 
