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
ms.openlocfilehash: 37c6e87ea50f3978bb896c7896a41b2faa9798bc
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566972"
---
# <a name="global-assembly-cache"></a>Genel Derleme Önbelleği
Ortak dil çalışma zamanının yüklü olduğu her bilgisayarda, genel derleme önbelleği olarak adlandırılan makine genelindeki bir kod önbelleği bulunur. Genel bütünleştirilmiş kod önbelleği, bilgisayardaki çeşitli uygulamalar tarafından paylaşılmak üzere özel olarak belirlenmiş derlemeleri depolar.  
  
 Derlemeleri yalnızca gerektiğinde genel derleme önbelleğine yükleyerek paylaşabilirsiniz. Genel bir kılavuz olarak, derleme bağımlılıklarını özel tutun ve bir derlemeyi paylaşıma açık bir şekilde gerekmediği sürece derlemeleri uygulama dizininde bulun. Ayrıca, COM birlikte çalışma veya yönetilmeyen kod için erişilebilir hale getirmek üzere derlemeleri genel derleme önbelleğine yüklemek gerekli değildir.  
  
> [!NOTE]
>  Genel bütünleştirilmiş kod önbelleğine bir derlemeyi doğrudan yüklemek istemediğiniz senaryolar vardır. Genel derleme önbelleğinde bir uygulamayı oluşturan derlemelerden birini yerleştirirseniz, uygulama dizinini kopyalamak için **xcopy** komutunu kullanarak uygulamayı artık çoğaltamaz veya yükleyemezsiniz. Derlemeyi genel derleme önbelleğinde de taşımanız gerekir.  
  
 Bir derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtmanın iki yolu vardır:  
  
- Genel derleme önbelleği ile çalışmak için tasarlanan bir yükleyici kullanın. Bu, bütünleştirilmiş kodları genel derleme önbelleğine yüklemek için tercih edilen seçenektir.  
  
- Windows SDK tarafından verilen [genel derleme önbelleği aracı (Gacutil. exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)adlı bir geliştirici aracı kullanın.  
  
    > [!NOTE]
    >  Dağıtım senaryolarında, bütünleştirilmiş kodları genel derleme önbelleğine yüklemek için Windows Installer kullanın. Genel bütünleştirilmiş kod önbelleği aracını yalnızca geliştirme senaryolarında kullanın, çünkü bu, Windows Installer kullanılırken belirtilen derleme başvuru sayma ve diğer özellikleri sağlamıyor.  
  
 .NET Framework 4 ' te başlayarak, genel derleme önbelleğinin varsayılan konumu **%windir%\Microsoft.NET\assembly**' dir. .NET Framework önceki sürümlerinde, varsayılan konum **%windir%\Assembly**' dir.  
  
 Yöneticiler, yazma ve Yürütme erişimini denetlemek için genellikle bir erişim denetim listesi (ACL) kullanarak SystemRoot dizinini korur. Genel derleme önbelleği, SystemRoot dizininin bir alt dizininde yüklü olduğundan, bu dizinin ACL 'sini devralır. Yalnızca yönetici ayrıcalıklarına sahip kullanıcıların, dosyaları genel derleme önbelleğinden silmesine izin verilmesi önerilir.  
  
 Genel bütünleştirilmiş kod önbelleğinde dağıtılan derlemelerin tanımlayıcı bir adı olmalıdır. Genel bütünleştirilmiş kod önbelleğine bir derleme eklendiğinde, derlemeyi oluşturan tüm dosyalarda bütünlük denetimleri gerçekleştirilir. Önbellek, bir derlemenin değiştirilmediğinden emin olmak için bu bütünlük denetimlerini gerçekleştirir, örneğin bir dosya değiştiğinde bildirim değişikliği yansıtmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)
