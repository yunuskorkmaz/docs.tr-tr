---
title: Birlikte Çalışma Projesi Derleme
description: İçeri aktarılan COM türlerini içeren bir veya daha fazla derlemeye başvurduklarında, yönetilen projeler gibi derlenen bir COM birlikte çalışma projesinin nasıl derlendiğini gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
ms.openlocfilehash: 1cf5bdbedd53227e812b0d2ed97778ab34a81444
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557103"
---
# <a name="compiling-an-interop-project"></a>Birlikte Çalışma Projesi Derleme

İçeri aktarılan COM türlerini içeren bir veya daha fazla derlemeye başvuran COM birlikte çalışma projeleri, diğer yönetilen projeler gibi derlenir. Birlikte Çalışma Derlemeleriyle Visual Studio gibi bir geliştirme ortamında başvurabilirsiniz veya bir komut satırı derleyicisi kullandığınızda bunlara başvurabilirsiniz. Her iki durumda da, düzgün bir şekilde derlemek için birlikte çalışma derlemesinin diğer proje dosyalarıyla aynı dizinde olması gerekir.

 Birlikte çalışma derlemelerine başvurmanın iki yolu vardır:

- Gömülü birlikte çalışma türleri: .NET Framework 4 ve Visual Studio 2010 ile başlayarak, derleyicinin tür bilgilerini yürütülebilir bir derlemeden çalıştırılabilire katıştırmasını isteyebilirsiniz. Önerilen yöntem budur.

- Birlikte çalışma derlemelerini dağıtma: birlikte çalışabilirlik derlemesine standart bir başvuru oluşturabilirsiniz. Bu durumda, birlikte çalışma derlemesinin uygulamanızla birlikte dağıtılması gerekir.

 Bu iki teknik arasındaki farklılıklar, [yönetilen KODDAKI com türlerini kullanmayla](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))daha ayrıntılı bir şekilde ele alınmıştır.

 Visual Studio ile birlikte çalışma türlerini katıştırma [Izlenecek yol: Visual Studio 'Da yönetilen derlemelerden tür ekleme](../../standard/assembly/embed-types-visual-studio.md)gösterilmektedir.

 Bir komut satırı derleyicisi ile birlikte çalışma derlemesine başvurmak ve tür bilgilerini çalıştırılabilirlerinizde eklemek için [-Link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici anahtarını kullanın ve birlikte çalışma derlemesinin adını belirtin.

> [!NOTE]
> Visual C++ uygulamalar tür bilgilerini katıştıramazlar, ancak bunu yapan uygulamalarla veya eklentilerle birlikte çalışabilir.

 Birincil birlikte çalışma derlemesini içeren bir uygulamayı dağıtıldığında derlemek için **/Reference** derleyici anahtarını kullanın ve birlikte çalışma derlemesinin adını belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../standard/language-independence-and-language-independent-components.md)
- [Yönetilen kodda COM türlerini kullanma](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [İzlenecek yol: Visual Studio’da Yönetilen Bütünleştirilmiş Kodlardan Türleri Katıştırma](../../standard/assembly/embed-types-visual-studio.md)
- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
