---
title: "Nasıl yapılır: Windows API'larını Çağırma (Visual Basic)"
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: de568c3273d4d040c6566136e5d59e2155b86f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643646"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Nasıl yapılır: Windows API'larını Çağırma (Visual Basic)
Bu örnek tanımlar ve çağırır `MessageBox` user32.dll işlevinde ve bir dize geçirir.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir başvuru <xref:System> ad alanı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yöntemi statik değil, Özet veya önceden tanımlanmış. Bir arabirim ya da uzunluğu üst türüdür *adı* veya *dll* sıfırdır. (<xref:System.ArgumentException>)  
  
-   *Adı* veya *dll* olan `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   İçeren türü kullanılarak önceden oluşturuldu `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yakından Platform çağırma](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [Platform Çağırma Örnekleri](../../../framework/interop/platform-invoke-examples.md)  
 [Yönetilmeyen DLL İşlevlerini Kullanma](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [Yansıma ile bir yöntem tanımlama yayma](http://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [İzlenecek yol: Windows API'lerini Çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
