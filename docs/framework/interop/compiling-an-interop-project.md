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
ms.openlocfilehash: 37dda10a3dcbcb0968674e04292c5dc1a79be66f
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69013012"
---
# <a name="compiling-an-interop-project"></a>Birlikte Çalışma Projesi Derleme

İçeri aktarılan COM türlerini içeren bir veya daha fazla derlemeye başvuran COM birlikte çalışma projeleri, diğer yönetilen projeler gibi derlenir. Birlikte Çalışma Derlemeleriyle Visual Studio gibi bir geliştirme ortamında başvurabilirsiniz veya bir komut satırı derleyicisi kullandığınızda bunlara başvurabilirsiniz. Her iki durumda da, düzgün bir şekilde derlemek için birlikte çalışma derlemesinin diğer proje dosyalarıyla aynı dizinde olması gerekir.

 Birlikte çalışma derlemelerine başvurmanın iki yolu vardır:

- Gömülü birlikte çalışma türleri: .NET Framework 4 ve Visual Studio 2010 ile başlayarak, derleyicinin tür bilgilerini yürütülebilir bir derlemeden çalıştırılabilire katıştırmasını isteyebilirsiniz. Önerilen yöntem budur.

- Birlikte çalışma derlemelerini dağıtma: Birlikte çalışabilirlik derlemesine standart bir başvuru oluşturabilirsiniz. Bu durumda, birlikte çalışma derlemesinin uygulamanızla birlikte dağıtılması gerekir.

 Bu iki teknik arasındaki farklılıklar, [yönetilen KODDAKI com türlerini kullanmayla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))daha ayrıntılı bir şekilde ele alınmıştır.

 Birlikte çalışma türlerini Visual Studio [ile katıştırma izlenecek yol: Visual StudioC#](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)'daki yönetilen derlemelerden türler ekleme ve [izlenecek yol: Visual Studio 'da yönetilen derlemelerden türler ekleme (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).

 Bir komut satırı derleyicisi ile birlikte çalışma derlemesine başvurmak ve tür bilgilerini çalıştırılabilirlerinizde eklemek için, [/Link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici anahtarını kullanın ve birlikte çalışma derlemesinin adını belirtin.

> [!NOTE]
> Görsel C++ uygulamalar tür bilgilerini katıştıramazlar, ancak bunu yapan uygulamalarla veya eklentilerle birlikte çalışabilir.

 Birincil birlikte çalışma derlemesini içeren bir uygulamayı dağıtıldığında derlemek için **/Reference** derleyici anahtarını kullanın ve birlikte çalışma derlemesinin adını belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../standard/language-independence-and-language-independent-components.md)
- [Yönetilen kodda COM türlerini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [İzlenecek yol: Visual Studio 'da yönetilen derlemelerden tür ekleme (C#)](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [İzlenecek yol: Visual Studio 'da yönetilen derlemelerden tür ekleme (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
