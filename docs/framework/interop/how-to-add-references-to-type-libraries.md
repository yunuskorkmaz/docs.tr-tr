---
title: 'Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 561e05c82c1882ad5e495ddb3dc1a17356522514
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-references-to-type-libraries"></a>Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme
Visual Studio bir tür kitaplığı başvuru eklediğinizde, meta verileri içeren bir birlikte çalışma derleme oluşturur. Birincil birlikte çalışma derlemesi varsa, Visual Studio yeni bir birlikte çalışma derleme oluşturmadan önce varolan derleme kullanır.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Visual Studio'da bir tür kitaplığı için bir başvuru eklemek için  
  
1.  Bir Windows Setup.exe dosyasını yükleme sizin için gerçekleştirir sürece, bilgisayarınızdaki COM DLL veya EXE dosyasını yükleyin.  
  
2.  Seçin **proje**, **başvuru ekleme**.  
  
3.  Başvuru Yöneticisi'nde seçin **COM**.  
  
4.  Tür kitaplığını listeden seçin veya .tlb dosyasına göz atın.  
  
5.  Seçin **Tamam**.  
  
6.  Çözüm Gezgini'nde eklenen yeni başvuru için kısayol menüsünü açın ve ardından **özellikleri**.  
  
7.  İçinde **özellikleri** penceresinde olduğundan emin olun **birlikte çalışma türlerini katıştır** özelliği ayarlanmış **doğru**. Bu, uygulamanız ile birincil birlikte çalışma derlemeleri dağıtma gereğini ortadan kaldırır, yürütülebilir dosyalarında COM türleri için tür bilgisi katıştırmak Visual Studio neden olur.  
  
> [!NOTE]
>  Menü ve iletişim kutusu seçenekleri kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak değişebilir.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Komut satırı derleme için bir tür kitaplığı için bir başvuru eklemek için  
  
1.  Birlikte çalışma bütünleştirilmiş açıklandığı gibi oluşturmak [nasıl yapılır: tür kitaplıklarından birlikte çalışma derlemeleri oluşturmak](how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2.  Kullanım [/Link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) COM tür bilgileri katıştırmak için derleyici seçeneği ile birlikte çalışma derleme adı türleri, yürütülebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)  
 [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)  
 [İzlenecek yol: Microsoft Office Bütünleştirilmiş Kodlarından Tür Bilgilerini Katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))  
 [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [/ Link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [/ Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
