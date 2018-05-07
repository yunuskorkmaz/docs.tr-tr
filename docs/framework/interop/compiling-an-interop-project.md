---
title: Birlikte Çalışma Projesi Derleme
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6099764fb98604726da99ef71b9c82e9a931bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="compiling-an-interop-project"></a>Birlikte Çalışma Projesi Derleme
İçeri aktarılan COM türlerini içeren bir veya daha fazla derlemeler başvuru COM birlikte çalışma projelerini gibi yönetilen diğer proje derlenir. Visual Studio gibi geliştirme ortamında birlikte çalışma derlemeleri başvurusu yapabilir veya komut satırı derleyicisi kullandığınızda başvurabilir. Her iki durumda da, diğer proje dosyaları ile aynı dizinde birlikte çalışma derlemesi düzgün derlemek için olmalıdır.  
  
 Birlikte çalışma derlemeleri başvurmak iki yolu vardır:  
  
-   Katıştırılmış birlikte çalışma türleri: itibaren [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ve [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], yürütülebilir dosyanın birlikte çalışma derlemeye tür bilgilerini katıştırma görevlendirin. Önerilen yöntem budur.  
  
-   Birlikte çalışma derlemeleri dağıtma: birlikte çalışma derlemesi için standart bir başvuru oluşturabilirsiniz. Bu durumda, uygulamanız ile birlikte çalışma derlemesi dağıtılmalıdır.  
  
 Bu iki teknikler arasındaki farklar daha ayrıntılı olarak ele alınmıştır [COM türlerinde kullanarak yönetilen kod](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).  
  
 Visual Studio ile birlikte çalışma türlerini katıştırma içinde gösterilmiştir [izlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) ve [izlenecek yol: yönetilen derlemelerden türler katıştırma](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 Komut satırı derleyicisi ile birlikte çalışma bir derleme başvurusu, yürütülebilir tür bilgilerini katıştırma, kullanın ve [/Link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici anahtar ve birlikte çalışma derlemesinin adını belirtin.  
  
> [!NOTE]
>  Visual C++ uygulamalarını tür bilgilerini katıştırma olamaz, ancak uygulamalar veya yapmak eklentileri ile çalışabilirler.  
  
 Birincil birlikte çalışma derlemesi dağıtıldığında içeren bir uygulama derlemek için kullanmak **/reference** derleyici geçin ve birlikte çalışma derlemesinin adını belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)  
 [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../standard/language-independence-and-language-independent-components.md)  
 [Yönetilen kodda COM türlerini kullanma](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))  
 [İzlenecek yol: Microsoft Office Bütünleştirilmiş Kodlarından Tür Bilgilerini Katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))  
 [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
