---
title: 'Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme'
description: Visual Studio 'da veya komut satırı derlemesinde tür kitaplıklarına nasıl başvurular ekleneceğini anlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: a3c24385c9cc7debe95aa10369b050897415bc46
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617437"
---
# <a name="how-to-add-references-to-type-libraries"></a>Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme
Visual Studio, bir tür kitaplığına bir başvuru eklediğinizde meta verileri içeren bir birlikte çalışma derlemesi oluşturur. Birincil birlikte çalışma derlemesi varsa, Visual Studio yeni bir birlikte çalışma derlemesi oluşturmadan önce mevcut derlemeyi kullanır.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Visual Studio 'da bir tür kitaplığına başvuru eklemek için  
  
1. Bir Windows Setup.exe dosyası yüklemeyi sizin için gerçekleştirmediği takdirde, COM DLL veya EXE dosyasını bilgisayarınıza yükleyebilirsiniz.  
  
2. **Proje**, **Başvuru Ekle**' yi seçin.  
  
3. Başvuru Yöneticisi 'nde **com**' u seçin.  
  
4. Listeden tür kitaplığını seçin veya. tlb dosyasına gözatamazsınız.  
  
5. **Tamam ' ı**seçin.  
  
6. Çözüm Gezgini ' de, yeni eklediğiniz başvurunun kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
7. **Özellikler** penceresinde, **birlikte çalışma türlerini katıştır** özelliğinin **true**olarak ayarlandığından emin olun. Bu, Visual Studio 'Nun çalıştırılabilirlerinizdeki COM türlerine ait tür bilgilerini katıştırmasına ve birincil birlikte çalışma derlemelerini uygulamanızla birlikte dağıtma gereksinimini ortadan kaldırmaya neden olur.  
  
> [!NOTE]
> Menü ve iletişim kutusu seçenekleri, kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak farklılık gösterebilir.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Komut satırı derlemesi için bir tür kitaplığına başvuru eklemek için  
  
1. [Nasıl yapılır: tür kitaplıklarından birlikte çalışma derlemeleri oluşturma](how-to-generate-interop-assemblies-from-type-libraries.md)bölümünde açıklandığı gibi bir birlikte çalışma derlemesi oluşturun.  
  
2. Çalıştırılabilirlerinizde COM türlerine ilişkin tür bilgilerini eklemek için [-Link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici seçeneğini birlikte çalışma derleme adıyla birlikte kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [İzlenecek yol: Visual Studio’da Yönetilen Bütünleştirilmiş Kodlardan Türleri Katıştırma](../../standard/assembly/embed-types-visual-studio.md)
- [-Link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-bağlantı (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
