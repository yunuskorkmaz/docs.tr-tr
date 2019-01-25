---
title: 'Nasıl yapılır: Tür kitaplıklarına başvurular ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebd7599205206e026c7de7b4e7bc2e5352771bd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522225"
---
# <a name="how-to-add-references-to-type-libraries"></a>Nasıl yapılır: Tür kitaplıklarına başvurular ekleme
Visual Studio, bir tür kitaplığına bir başvuru eklediğinizde, meta verileri içeren bir birlikte çalışma derlemesi oluşturur. Visual Studio, bir birincil birlikte çalışma derlemesi varsa, yeni bir birlikte çalışma bütünleştirilmiş kodu oluşturuluyor önce mevcut bütünleştirilmiş kodu kullanır.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Visual Studio'da bir tür kitaplığına bir başvuru eklemek için  
  
1.  Bir Windows Setup.exe dosyasını yükleme sizin için gerçekleştirir, bilgisayarınızda COM DLL veya EXE dosyasının yükleyin.  
  
2.  Seçin **proje**, **Başvurusu Ekle**.  
  
3.  Başvuru Yöneticisi'nde seçin **COM**.  
  
4.  Tür kitaplığını listeden seçin veya .tlb dosyasına göz at.  
  
5.  **Tamam**’ı seçin.  
  
6.  Çözüm Gezgini içinde eklenen yeni başvuru için kısayol menüsünü açın ve ardından **özellikleri**.  
  
7.  İçinde **özellikleri** penceresinde emin **birlikte çalışma türlerini katıştır** özelliği **True**. Bu, uygulamanız ile birincil birlikte çalışma derlemelerini dağıtma gereksinimini ortadan kaldıran, yürütülebilir dosyaları, COM türleri için tür bilgisi katıştırma Visual Studio neden olur.  
  
> [!NOTE]
>  Menü ve iletişim kutusu seçenekleri, kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak değişiklik gösterebilir.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Komut satırı derlemesi için bir tür kitaplığına bir başvuru eklemek için  
  
1.  Birlikte çalışma derlemesi açıklandığı gibi oluşturmak [nasıl yapılır: Tür kitaplıklarından birlikte çalışma derlemeleri oluşturma](how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2.  Kullanım [/link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) COM için tür bilgilerini katıştırma derleyici seçeneğiyle birlikte çalışma bütünleştirilmiş kod adı, yürütülebilir dosyaların türleri.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [İzlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))
- [İzlenecek yol: Yönetilen derlemelerden türler katıştırma](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)
- [/ Link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [/ Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
