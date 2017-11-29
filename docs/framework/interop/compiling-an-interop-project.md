---
title: "Birlikte Çalışma Projesi Derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc541911670c533caa97c645085ad09bde5eefdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="compiling-an-interop-project"></a>Birlikte Çalışma Projesi Derleme
İçeri aktarılan COM türlerini içeren bir veya daha fazla derlemeler başvuru COM birlikte çalışma projelerini gibi yönetilen diğer proje derlenir. Visual Studio gibi geliştirme ortamında birlikte çalışma derlemeleri başvurusu yapabilir veya komut satırı derleyicisi kullandığınızda başvurabilir. Her iki durumda da, diğer proje dosyaları ile aynı dizinde birlikte çalışma derlemesi düzgün derlemek için olmalıdır.  
  
 Birlikte çalışma derlemeleri başvurmak iki yolu vardır:  
  
-   Katıştırılmış birlikte çalışma türleri: itibaren [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ve [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], yürütülebilir dosyanın birlikte çalışma derlemeye tür bilgilerini katıştırma görevlendirin. Önerilen yöntem budur.  
  
-   Birlikte çalışma derlemeleri dağıtma: birlikte çalışma derlemesi için standart bir başvuru oluşturabilirsiniz. Bu durumda, uygulamanız ile birlikte çalışma derlemesi dağıtılmalıdır.  
  
 Bu iki teknikler arasındaki farklar daha ayrıntılı olarak ele alınmıştır [COM türlerinde kullanarak yönetilen kod](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).  
  
 Visual Studio ile birlikte çalışma türlerini katıştırma içinde gösterilmiştir [izlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) ve [izlenecek yol: yönetilen derlemelerden türler katıştırma](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 Komut satırı derleyicisi ile birlikte çalışma bir derleme başvurusu, yürütülebilir tür bilgilerini katıştırma, kullanın ve [/Link (C# Derleyici Seçenekleri)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) derleyici anahtar ve birlikte çalışma derlemesinin adını belirtin.  
  
> [!NOTE]
>  Visual C++ uygulamalarını tür bilgilerini katıştırma olamaz, ancak uygulamalar veya yapmak eklentileri ile çalışabilirler.  
  
 Birincil birlikte çalışma derlemesi dağıtıldığında içeren bir uygulama derlemek için kullanmak **/reference** derleyici geçin ve birlikte çalışma derlemesinin adını belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM bileşenlerini .NET Framework'te gösterme](../../../docs/framework/interop/exposing-com-components.md)  
 [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [Yönetilen kodda COM türlerini kullanma](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [İzlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [İzlenecek yol: Yönetilen derlemelerden türler katıştırma](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [Tür kitaplığını derleme olarak içeri aktarma](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
