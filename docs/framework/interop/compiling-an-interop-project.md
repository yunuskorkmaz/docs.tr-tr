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
ms.openlocfilehash: 5a1e6ea8a7a7e6869ca9bc6c1b635f30574ac97f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695200"
---
# <a name="compiling-an-interop-project"></a>Birlikte Çalışma Projesi Derleme

İçeri aktarılan COM türlerini içeren bir veya daha fazla derlemelerine COM birlikte çalışma projelerini gibi yönetilen diğer proje derlenir. Visual Studio gibi geliştirme ortamında birlikte çalışma derlemelerini başvurabilir veya bir komut satırı derleyicisini kullanarak başvurabilirsiniz. Her iki durumda da, diğer proje dosyaları ile aynı dizinde birlikte çalışma derlemesi doğru şekilde derlenmesi için olmalıdır.

 Birlikte çalışma derlemelerini başvurmak için iki yolu vardır:

-   Gömülü birlikte çalışma türleri: İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ve Visual Studio 2010, derleyicinin tür bilgilerini birlikte çalışma bütünleştirilmiş kod yürütülebilir dosyanın içine gömmek için cmdlet'ten. Önerilen yöntem budur.

-   Birlikte çalışma derlemelerini dağıtma: Standart bir birlikte çalışma derlemesine başvuru oluşturabilirsiniz. Bu durumda, birlikte çalışma derlemesi uygulamanızla dağıtılması gerekir.

 Bu iki teknik arasındaki farkları daha ayrıntılı olarak ele alınmıştır [kullanarak, yönetilen kodda COM türlerini](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).

 Visual Studio ile birlikte çalışma türlerini katıştırma içinde gösterilmiştir [izlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) ve [izlenecek yol: Yönetilen derlemeler türler katıştırma](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).

 Bir komut satırı derleyicisi ile birlikte çalışma derlemesine başvurmak ve, yürütülebilir dosyaların tür bilgilerini katıştırma için kullandığınız [/Link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici anahtarını ve birlikte çalışma derlemesi adı belirtin.

> [!NOTE]
> Visual C++ uygulamalarını tür bilgileri katıştırılamıyor ancak uygulamaları veya yapan eklentiler ile çalışabilirler.

 Birincil birlikte çalışma derlemesi dağıtıldığında içeren bir uygulama derlemek için kullanın **/reference** derleyici geçiş ve birlikte çalışma derlemesi adı belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../standard/language-independence-and-language-independent-components.md)
- [Yönetilen kodda COM türlerini kullanma](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))
- [İzlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))
- [İzlenecek yol: Yönetilen derlemelerden türler katıştırma](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)
- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)