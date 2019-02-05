---
title: "Nasıl yapılır: (Visual Basic) Windows API'lerini çağırma"
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 9eb667c8492c1e20b82e16ae8d640aee872969e5
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738649"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Nasıl yapılır: (Visual Basic) Windows API'lerini çağırma
Bu örnekte, tanımlar ve çağrı `MessageBox` user32.dll işlevi ve bir dize geçirir.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir başvuru <xref:System> ad alanı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yöntem statik değil, Özet veya önceden tanımlanmış. Üst türü bir arabirim veya uzunluğu olan *adı* veya *dll* sıfırdır. (<xref:System.ArgumentException>)  
  
-   *Adı* veya *dll* olduğu `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   Kapsayan türü kullanılarak önceden oluşturuldu `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yakından Platform çağırma](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Platform Çağırma Örnekleri](../../../framework/interop/platform-invoke-examples.md)
- [Yönetilmeyen DLL İşlevlerini Kullanma](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Yayma yansıma ile bir yöntem tanımlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [İzlenecek yol: Windows API'lerini Çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
