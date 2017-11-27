---
title: "XAML Güvenlik Konuları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 59d0b835a0de3e84e2cb6e77ed368511bfe21b19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-security-considerations"></a>XAML Güvenlik Konuları
XAML ve .NET Framework XAML Hizmetleri API kullandığınızda, bu konuda uygulamalarında güvenlik için en iyi uygulamaları açıklar.  
  
## <a name="untrusted-xaml-in-applications"></a>Güvenilmeyen XAML uygulamaları içinde  
 En genel anlamda güvenilmeyen XAML uygulamanızı özellikle ekleyen veya yayma herhangi bir XAML kaynağı ' dir.  
  
 İçine derlenmiş veya olarak depolanan XAML bir `resx`-güvenilir ve imzalı bir derleme içinde tür kaynak kendiliğinden güvenilmeyen değil. Derleme bir bütün olarak güven kadar XAML güvenebilirsiniz. Çoğu durumda, yalnızca bir akış veya diğer GÇ yük XAML kaynağı gevşek XAML güven yönlerini ile ilgili. Gevşek XAML belirli bileşeni veya bir dağıtım ve paketleme altyapı ile bir uygulama modelinin özelliği değil. Ancak, bir derlemeyi gevşek XAML yüklemektir bir davranış uygulayabilir.  
  
 Güvenilmeyen kod değilmiş gibi güvenilmeyen XAML için bu genellikle aynı değerlendirmeniz gerekir. Korumalı alan veya diğer metaphors büyük olasılıkla güvenilmeyen XAML güvenilen kodunuzu erişimini engellemek için kullanın.  
  
 XAML yetenekleri yapısını XAML nesneleri oluşturmak ve bunların özelliklerini ayarlama hakkı verir. Eşleme ve İşaretleme uzantıları kullanarak derlemeler uygulama etki alanındaki erişme tür dönüştürücüleri erişme bu yetenekleri de dahil `x:Code` blokları ve benzeri.  
  
 Kendi dil düzeyi özelliklere ek olarak birçok teknolojileri UI tanımında için XAML kullanılır. Güvenilmeyen XAML yüklenirken, kötü amaçlı bir kimlik sahtekarlığı UI yüklenirken anlamına gelebilir.  
  
## <a name="sharing-context-between-readers-and-writers"></a>Bağlam okuyucuları ve yazıcıları arasında paylaşma  
 XAML okuyucuları ve XAML yazarları için .NET Framework XAML Hizmetleri mimarisi, genellikle bir XAML okuyucu XAML yazan veya bir paylaşılan XAML şema içeriği paylaşma gerektirir. Nesneleri veya bağlamları paylaşımı XAML düğüm döngü mantığı yazmak veya özel bir sağlama kaydederseniz yol gerekli olabilir. XAML okuyucu örnekleri, varsayılan olmayan XAML şema içeriği ya da XAML okuyucu/yazan sınıflar arasında güvenilir ve güvenilir olmayan kod ayarlarını paylaşmamalıdır.  
  
 Çoğu senaryo ve destekleyen bir CLR tabanlı türü için yazma XAML nesneyle ilgili işlemleri yalnızca varsayılan XAML şema içeriği kullanabilirsiniz. Varsayılan XAML şema içeriği tam güven tehlikeye atabilecek ayarları açıkça içermez. Bu nedenle, bağlam güvenilen ve güvenilmeyen XAML Okuyucu/Yazıcı bileşenleri arasında paylaşmak güvenlidir. Bunu yaparsanız, ancak bunu hala böyle okuyucuları ve yazıcıları ayrı tutmak için en iyi uygulamadır <xref:System.AppDomain> kapsamlarla, özellikle amaçlayan/kısmi güven için korumalı bunlardan biri.  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>XAML ad uzayları ve derleme güven  
 Temel nitelenmemiş sözdizimi ve XAML özel bir XAML ad alanı eşleme bir derleme yorumlaması için tanım ayırt arasında güvenilir ve güvenilir olmayan bir derleme uygulama etki alanına yüklü olarak. Bu nedenle, güvenilmeyen bütünleştirilmiş güvenilen derlemenin hedeflenen XAML ad alanı eşlemesi aldatma ve XAML kaynağının bildirilen nesne ve özellik bilgileri yakalamak teknik olarak mümkündür. Bu durumu önlemek için güvenlik gereksinimleri varsa, aşağıdaki yöntemlerden birini kullanarak, hedeflenen XAML ad alanı eşlemesi yapılmalıdır:  
  
-   Uygulamanızın XAML tarafından yapılan tüm XAML ad alanı eşlemesi güçlü adla bir tam nitelikli derleme adı kullanın.  
  
-   Belirli bir oluşturarak başvuru derlemeleri, sabit bir dizi eşleme derleme kısıtlamak <xref:System.Xaml.XamlSchemaContext> için XAML okuyucuları ve XAML yazıcılarının nesnesi. Bkz: <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>XAML tür eşlemesi ve tür sistem erişimi  
 XAML olan birçok yolla CLR temel CLR tür sistemi nasıl uyguladığını eşe kendi tür sistemi destekler. Ancak, belirli yönlerini türü tanıma burada kendi türü bilgilerine dayalı bir tür güven kararlardan yapmak için türlerini destekleyen CLR türü bilgileri erteleneceği. XAML tür sistemi belirli raporlama özelliklerinin bazıları sanal yöntemleri olarak açık kalır ve bu nedenle, tam olarak özgün .NET Framework XAML hizmetlerinde uygulamaları denetimi altında olmayan olmasıdır. XAML tür sistemi XAML kendisini genişletilebilirlik ve varsayılan XAML şema içeriği ve varsayılan CLR destekli uygulaması yerine kendi olası alternatif türü eşlemesi stratejileri eşleşecek şekilde genişletilebilir olduğundan bu genişletilebilirlik noktaları yok. Daha fazla bilgi için özel notlar birkaç özelliklerini görmek <xref:System.Xaml.XamlType> ve <xref:System.Xaml.XamlMember>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xaml.Permissions.XamlAccessLevel>
