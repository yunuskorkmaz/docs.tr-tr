---
title: "Nasıl yapılır: Windows API'lerini Çağırma"
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 863986e94855e02e9fd04685f7dc3e8e7f7b1cc3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548071"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Nasıl yapılır: Windows API'larını Çağırma (Visual Basic)
Bu örnek, user32.dll işlevi tanımlar ve çağırır `MessageBox` ve sonra bir String öğesine geçirir.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>Kodu derle  
 Bu örnek şunları gerektirir:  
  
- <xref:System>Ad alanına başvuru.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yöntem statik değil, soyut veya daha önce tanımlanmış. Üst tür bir arabirimdir, ya da *ad* veya *DLL* uzunluğu sıfırdır. (<xref:System.ArgumentException>)  
  
- Ad veya *DLL* *adı* `Nothing` . (<xref:System.ArgumentNullException>)  
  
- İçeren tür önceden kullanılarak oluşturulmuştur `CreateType` . (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Platform çağırma ' ye daha yakından bakış](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Platform Çağırma Örnekleri](../../../framework/interop/platform-invoke-examples.md)
- [Yönetilmeyen DLL İşlevlerini Kullanma](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Yansıma Yayma ile bir yöntem tanımlama](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [İzlenecek yol: Windows API'lerini Çağırma](walkthrough-calling-windows-apis.md)
- [COM birlikte çalışma](index.md)
