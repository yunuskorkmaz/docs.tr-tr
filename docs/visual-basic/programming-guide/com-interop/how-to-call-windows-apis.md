---
title: "Nasıl yapılır: Windows API'larını Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 772db789fba4552a4645d2c6a242ba01944652ee
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
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
