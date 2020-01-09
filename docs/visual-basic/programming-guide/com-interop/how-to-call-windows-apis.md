---
title: "Nasıl yapılır: Windows API'larını Çağırma"
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 9de9f0fbcca291af0b6aadfd8e3fe7033708fbc6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347541"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Nasıl yapılır: Windows API'larını Çağırma (Visual Basic)
Bu örnek, User32. dll ' de `MessageBox` işlevini tanımlar ve çağırır ve sonra buna bir dize geçirir.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu örnek şunları gerektirir:  
  
- <xref:System> ad alanına bir başvuru.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yöntem statik değil, soyut veya daha önce tanımlanmış. Üst tür bir arabirimdir, ya da *ad* veya *DLL* uzunluğu sıfırdır. (<xref:System.ArgumentException>)  
  
- Ad veya *DLL* *adı* `Nothing`. (<xref:System.ArgumentNullException>)  
  
- Kapsayan tür daha önce `CreateType`kullanılarak oluşturulmuştur. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Platform çağırma ' ye daha yakından bakış](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Platform Çağırma Örnekleri](../../../framework/interop/platform-invoke-examples.md)
- [Yönetilmeyen DLL İşlevlerini Kullanma](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Yansıma Yayma ile bir yöntem tanımlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [İzlenecek yol: Windows API'lerini Çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
