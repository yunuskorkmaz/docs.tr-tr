---
title: "Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e80c4bf5142a9bbbd2b7f75d67553db73f0ff22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
  
1.  Birlikte çalışma bütünleştirilmiş açıklandığı gibi oluşturmak [nasıl yapılır: tür kitaplıklarından birlikte çalışma derlemeleri oluşturmak](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2.  Kullanım [/Link (C# Derleyici Seçenekleri)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) COM tür bilgileri katıştırmak için derleyici seçeneği ile birlikte çalışma derleme adı türleri, yürütülebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [COM Bileşenlerini .NET Framework'te Gösterme](../../../docs/framework/interop/exposing-com-components.md)  
 [İzlenecek yol: Microsoft Office Bütünleştirilmiş Kodlarından Tür Bilgilerini Katıştırma](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [/ Link (C# Derleyici Seçenekleri)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md)  
 [/ Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md)
