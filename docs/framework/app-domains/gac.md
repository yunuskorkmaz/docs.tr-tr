---
title: "Genel Derleme Önbelleği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eedb33042bd904340cc02526c3f1cf927c09bd9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="global-assembly-cache"></a>Genel Derleme Önbelleği
Ortak dil çalışma zamanı yüklendiği her bilgisayarda, Genel Derleme Önbelleği'adında bir makine genelinde kod önbelleği bulunur. Genel Derleme Önbelleği özellikle bilgisayarda çeşitli uygulamalar tarafından paylaşılmak üzere belirtilen derlemelerini depolar.  
  
 Yalnızca, gerektiğinde bunları genel derleme önbelleğine yükleme tarafından derlemeleri paylaşması gerekir. Genel bir kılavuz olarak derleme bağımlılıkları gizliliğini korumak ve bir derlemeyi paylaşımı kesinlikle gerekli olmadığı sürece derlemeleri uygulama dizininde bulun. Buna ek olarak, COM birlikte çalışma veya yönetilmeyen kod için erişilebilir hale getirmek için genel derleme önbelleğine derlemelerini yüklemek gerekli değildir.  
  
> [!NOTE]
>  Açıkça bir derlemeyi genel derleme önbelleğine yükleme istediğiniz olmayan senaryolar vardır. Genel Derleme Önbelleği uygulamada oluşturan derlemeler birini yerleştirirseniz, artık çoğaltmak veya uygulamayı kullanarak yüklemek **xcopy** uygulama dizini kopyalamak için komutu. Derleme Genel Derleme Önbelleği'nde de taşımanız gerekir.  
  
 Bir derlemeyi genel derleme önbelleğine dağıtmanın iki yolu vardır:  
  
-   Genel Derleme Önbelleği ile çalışmak üzere tasarlanmış bir yükleyici kullanın. Derlemeleri genel derleme önbelleğine yükleme için tercih edilen seçenek budur.  
  
-   Adlı bir geliştirici aracı [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
    > [!NOTE]
    >  Derlemeleri genel derleme önbelleğine yükleme için Windows Installer dağıtım senaryolarında kullanın. Derleme başvurusu sayım ve Windows Installer kullanırken sağlanan diğer özellikleri sağlamadığından yalnızca geliştirme senaryolarda Genel Derleme Önbelleği Aracı'nı kullanın.  
  
 .NET Framework 4 ile başlayarak, genel derleme önbelleği için varsayılan konum olan **%windir%\Microsoft.NET\assembly**. .NET Framework önceki sürümlerde varsayılan konumdur **%windir%\assembly**.  
  
 Yöneticiler genellikle yazma denetlemek ve yürütme erişimi için bir erişim denetimi listesi (ACL) kullanılarak systemroot dizini koruyun. Genel Derleme Önbelleği systemroot dizinin bir alt dizinde yüklü olduğundan, bu dizinin ACL devralır. Yalnızca yönetici ayrıcalıklarına sahip kullanıcılar, Genel Derleme Önbelleği'nden dosyalarını silmek için izin önerilir.  
  
 Derlemeleri Genel Derleme Önbelleği'nde dağıtılan güçlü bir adı olması gerekir. Bir derlemeyi genel derleme önbelleği eklendiğinde, bütünlük denetimlerinin derlemeyi oluşturan tüm dosyalar üzerinde gerçekleştirilir. Önbellek, bir derlemeyi, örneğin, bir dosya değişti, ancak bildirim değişikliği yansıtmayan durumlarda değiştirilmemiş emin olmak için bu bütünlüğü denetler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)
