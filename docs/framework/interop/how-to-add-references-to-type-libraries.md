---
title: 'Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: 1e82a499b77cc6d1d49eaf13e243201bbdc4c5fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181440"
---
# <a name="how-to-add-references-to-type-libraries"></a>Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme
Visual Studio, tür kitaplığına bir başvuru eklediğinizde meta verileri içeren bir interop derlemesi oluşturur. Birincil interop derlemesi varsa, Visual Studio yeni bir interop derlemesi oluşturmadan önce varolan derlemeyi kullanır.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Visual Studio'daki tür kitaplığına başvuru eklemek için  
  
1. Bir Windows Setup.exe dosyası yüklemeyi sizin için gerçekleştirmedikçe, COM DLL veya EXE dosyasını bilgisayarınıza yükleyin.  
  
2. **Proje**seçin , **Referans Ekle**.  
  
3. Başvuru Yöneticisi'nde **COM'u**seçin.  
  
4. Listeden tür kitaplığını seçin veya .tlb dosyasına göz atın.  
  
5. **Tamam'ı**seçin.  
  
6. Çözüm Gezgini'nde, az önce eklediğiniz başvuru için kısayol menüsünü açın ve ardından **Özellikler'i**seçin.  
  
7. **Özellikler** penceresinde, **Embed Interop Türleri** özelliğinin **True**olarak ayarlandıkından emin olun. Bu, Visual Studio'nun çalıştırılabilir lerinize COM türleri için tür bilgilerini gömmesine neden olarak uygulamanızla birincil interop derlemeleri dağıtma gereksinimini ortadan kaldırır.  
  
> [!NOTE]
> Menü ve iletişim kutusu seçenekleri, kullandığınız Visual Studio sürümüne bağlı olarak değişebilir.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Komut satırı derlemesi için tür kitaplığına başvuru eklemek için  
  
1. Nasıl açıklandığı gibi bir interop derlemesi [oluşturun: Tür Kitaplıklarından Interop Derlemeleri Oluşturun.](how-to-generate-interop-assemblies-from-type-libraries.md)  
  
2. Yürütülebilirlerinize COM türleri için tür bilgilerini gömmek için interop montaj adı ile [-link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyicisi seçeneğini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [İzlenecek yol: Visual Studio’da Yönetilen Bütünleştirilmiş Kodlardan Türleri Katıştırma](../../standard/assembly/embed-types-visual-studio.md)
- [-link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-bağlantı (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
