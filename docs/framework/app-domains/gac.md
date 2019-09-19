---
title: Genel Derleme Önbelleği
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a2ac0c7fb5f89c7d6b9daba8da7b37d1135acb6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053179"
---
# <a name="global-assembly-cache"></a>Genel Derleme Önbelleği
Ortak dil çalışma zamanının yüklü olduğu her bilgisayarda, genel derleme önbelleği olarak adlandırılan makine genelindeki bir kod önbelleği bulunur. Genel bütünleştirilmiş kod önbelleği, bilgisayardaki çeşitli uygulamalar tarafından paylaşılmak üzere özel olarak belirlenmiş derlemeleri depolar.  
  
 Derlemeleri yalnızca gerektiğinde genel derleme önbelleğine yükleyerek paylaşabilirsiniz. Genel bir kılavuz olarak, derleme bağımlılıklarını özel tutun ve bir derlemeyi paylaşıma açık bir şekilde gerekmediği sürece derlemeleri uygulama dizininde bulun. Ayrıca, COM birlikte çalışma veya yönetilmeyen kod için erişilebilir hale getirmek üzere derlemeleri genel derleme önbelleğine yüklemek gerekli değildir.  
  
> [!NOTE]
> Genel bütünleştirilmiş kod önbelleğine bir derlemeyi doğrudan yüklemek istemediğiniz senaryolar vardır. Genel derleme önbelleğinde bir uygulamayı oluşturan derlemelerden birini yerleştirirseniz, uygulama dizinini kopyalamak için **xcopy** komutunu kullanarak uygulamayı artık çoğaltamaz veya yükleyemezsiniz. Derlemeyi genel derleme önbelleğinde de taşımanız gerekir.  
  
 Bir derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtmanın iki yolu vardır:  
  
- Genel derleme önbelleği ile çalışmak için tasarlanan bir yükleyici kullanın. Bu, bütünleştirilmiş kodları genel derleme önbelleğine yüklemek için tercih edilen seçenektir.  
  
- Windows SDK tarafından verilen [genel derleme önbelleği aracı (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md)adlı bir geliştirici aracı kullanın.  
  
    > [!NOTE]
    > Dağıtım senaryolarında, bütünleştirilmiş kodları genel derleme önbelleğine yüklemek için Windows Installer kullanın. Genel bütünleştirilmiş kod önbelleği aracını yalnızca geliştirme senaryolarında kullanın, çünkü bu, Windows Installer kullanılırken belirtilen derleme başvuru sayma ve diğer özellikleri sağlamıyor.  
  
 .NET Framework 4 ' te başlayarak, genel derleme önbelleğinin varsayılan konumu **%windir%\Microsoft.NET\assembly**' dir. .NET Framework önceki sürümlerinde, varsayılan konum **%windir%\Assembly**' dir.  
  
 Yöneticiler, yazma ve Yürütme erişimini denetlemek için genellikle bir erişim denetim listesi (ACL) kullanarak SystemRoot dizinini korur. Genel derleme önbelleği, SystemRoot dizininin bir alt dizininde yüklü olduğundan, bu dizinin ACL 'sini devralır. Yalnızca yönetici ayrıcalıklarına sahip kullanıcıların, dosyaları genel derleme önbelleğinden silmesine izin verilmesi önerilir.  
  
 Genel bütünleştirilmiş kod önbelleğinde dağıtılan derlemelerin tanımlayıcı bir adı olmalıdır. Genel bütünleştirilmiş kod önbelleğine bir derleme eklendiğinde, derlemeyi oluşturan tüm dosyalarda bütünlük denetimleri gerçekleştirilir. Önbellek, bir derlemenin değiştirilmediğinden emin olmak için bu bütünlük denetimlerini gerçekleştirir, örneğin bir dosya değiştiğinde bildirim değişikliği yansıtmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)
- [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](working-with-assemblies-and-the-gac.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../standard/assembly/strong-named.md)
