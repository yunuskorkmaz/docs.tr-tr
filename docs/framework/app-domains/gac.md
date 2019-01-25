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
ms.openlocfilehash: 15b258f0392275ffd18c52d11df3bc266a55ce3f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566300"
---
# <a name="global-assembly-cache"></a>Genel Derleme Önbelleği
Ortak dil çalışma zamanının yüklendiği her bilgisayarda, genel derleme önbelleği olarak adlandırılan bir makine düzeyinde kod önbelleği bulunur. Özellikle bilgisayarda çeşitli uygulamalar tarafından paylaşılmak üzere belirtilen derlemeleri genel derleme önbelleği depolar.  
  
 Derlemeleri için yalnızca ihtiyacınız olduğunda bunları genel bütünleştirilmiş kod önbelleğine yükleyerek paylaşmalısınız. Genel bir kılavuz olarak derleme bağımlılıklarını özel tutun ve derlemeyi paylaşmanız kesinlikle gerekli olmadığı sürece, derlemeleri uygulama dizinine yerleştirin. Ayrıca, derlemeleri COM birlikte çalışma veya yönetilmeyen koda erişilebilir hale getirmek için genel derleme önbelleğine yüklemek gerekli değildir.  
  
> [!NOTE]
>  Açıkça bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek istediğiniz olmayan senaryolar vardır. Genel Derleme Önbelleği uygulamayı oluşturan derlemeleri birini yerleştirirseniz, artık çoğaltmak veya uygulamayı kullanarak yüklemek **xcopy** uygulama dizinini kopyalamak için komutu. Derlemeyi de genel derleme önbelleğinde taşımanız gerekir.  
  
 Bir derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtmak için iki yolu vardır:  
  
-   Genel Derleme Önbelleği ile çalışmak üzere tasarlanmış bir yükleyici kullanın. Derlemeleri genel derleme önbelleğine yüklemek için tercih edilen seçenek budur.  
  
-   Adlı bir geliştirici araç [Genel Derleme Önbelleği aracını (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
    > [!NOTE]
    >  Dağıtım senaryolarında, derlemeleri genel derleme önbelleğine yüklemek için Windows Installer kullanın. Bütünleştirilmiş kod başvuru sayımı ve Windows Installer'ı kullanırken, sunulan diğer özellikleri sağlamaz çünkü yalnızca geliştirme senaryolarda, Genel Derleme Önbelleği aracını kullanın.  
  
 .NET Framework 4 ile başlayarak, genel derleme önbelleği için varsayılan konum olduğu **%windir%\Microsoft.NET\assembly**. Önceki .NET Framework sürümlerinde varsayılan konumdur **%windir%\assembly**.  
  
 Yöneticiler, erişim denetimi listesi (ACL) kullanarak yazma denetlemek ve yürütme erişimi systemroot dizinini genellikle koruyun. Genel bütünleştirilmiş kod önbelleği systemroot dizininin alt dizininde yüklü olduğu için dizinin ACL'sini devralır. Yalnızca yönetici ayrıcalıklarına sahip kullanıcılar, genel derleme önbelleğinden dosyaları silmek için izin önerilir.  
  
 Derlemeleri Genel Derleme Önbelleği'nde dağıtılan bir tanımlayıcı ad olmalıdır. Bir derlemeyi Genel Derleme Önbelleği'ne eklendiğinde, bütünlük kontrolleri derlemeyi oluşturan tüm dosyalar üzerinde gerçekleştirilir. Önbellek, bir derleme, örneğin, bir dosya değişmiş ancak bildirim değişikliği yansıtmaz oynanmadığını saptayabilmeleri emin olmak için bu bütünlük denetimi gerçekleştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)
