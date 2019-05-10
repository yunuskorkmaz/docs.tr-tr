---
title: XAML Güvenlik Konuları
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 76dce711e46d267c85b0fc9426be452d90b4d07c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622840"
---
# <a name="xaml-security-considerations"></a>XAML Güvenlik Konuları
Bu konuda, XAML ve .NET Framework XAML Hizmetleri API kullanırken uygulama güvenliği için en iyi uygulamalar açıklanmaktadır.  
  
## <a name="untrusted-xaml-in-applications"></a>Güvenilmeyen XAML uygulamalarında  
 En genel anlamda güvenilmeyen XAML, uygulamanızın özel olarak dahil etmek veya yayma tüm XAML kaynağıdır.  
  
 XAML ile derlenmiş veya olarak depolanan bir `resx`-güvenilen ve imzalı bir derleme içinde tür kaynak kendiliğinden güvenilmeyen değil. Bir bütün olarak derlemeyi güvendiğiniz kadar XAML güvenebilir. Çoğu durumda, yalnızca bir akış veya diğer g/ç yük bir XAML kaynak gevşek XAML güven yönlerini ile ilgili olursunuz. Gevşek XAML, belirli bir bileşen ya da bir uygulama modeli ile bir dağıtım ve paketleme altyapı özelliği değil. Ancak, bir derleme gevşek XAML yüklemektir bir davranış uygulayabilir.  
  
 Güvenilmeyen kod değilmiş gibi güvenilmeyen XAML için bu genellikle aynı kabul etmelidir. Korumalı alana alma veya diğer metaphors büyük olasılıkla güvenilmeyen XAML kodunuzu güvenilir erişimini engellemek için kullanın.  
  
 XAML özellikleri yapısını XAML nesneleri oluşturmak ve bunların özelliklerini ayarlamak hakkı verir. Bu özellikler de eşleme ve İşaretleme uzantıları kullanarak derlemeleri uygulama etki alanında erişmesini tür dönüştürücüleri erişme `x:Code` blokları ve benzeri.  
  
 Dil düzeyi özelliklerini ek olarak, XAML UI tanımı birçok teknolojileri için kullanılır. Güvenilmeyen XAML yükleniyor, kötü amaçlı bir kimlik sahtekarlığı UI yüklenirken anlamına gelebilir.  
  
## <a name="sharing-context-between-readers-and-writers"></a>Okuyucular ve yazıcılar arasında içerik paylaşımı  
 XAML okuyucular ve yazıcılar XAML için .NET Framework XAML hizmetlerinde mimarisi, genellikle bir XAML okuyucu XAML yazan ya da paylaşılan bir XAML şema içeriği paylaşımı gerektirir. Nesneleri veya bağlamları paylaşımı, XAML düğümü döngü mantığı yazıyorsunuz veya özel bir sağlama kaydederseniz yol gerekli olabilir. XAML okuyucu örnekleri, varsayılan XAML şema içeriği veya XAML okuyucu/yazan sınıflar arasında güvenilir ve güvenilir olmayan kod için ayarları paylaşmamalıdır.  
  
 Çoğu senaryoları ve destekleyen bir CLR tabanlı türü için yazma XAML nesneyle ilgili işlemleri yalnızca varsayılan XAML şema içeriği kullanabilirsiniz. Varsayılan XAML şema içeriği açıkça tam güven tehlikeye atabilecek ayarları içermez. Bu nedenle, güvenilir ve güvenilir olmayan XAML Okuyucu/Yazıcı bileşenleri arasında içerik paylaşmak güvenlidir. Bunu yaparsanız, ancak yine de böyle okuyucular ve yazıcılar ayrı tutmak için bir en iyi yöntemdir <xref:System.AppDomain> kapsamlar, özel olarak hedeflenen/kısmi güven için korumalı bunlardan biri ile.  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>XAML ad alanları ve bütünleştirilmiş kod güven  
 Temel nitelenmemiş sözdizimi ve XAML derleme için özel bir XAML ad alanı eşlemesi yorumlaması için tanım ayırt arasında güvenilir ve güvenilir olmayan bir derleme olarak bir uygulama etki alanına yüklenen. Bu nedenle, güvenilen bir derlemenin hedeflenen XAML ad alanı eşlemesi sızmasını ve XAML kaynağının bildirilen nesne ve özellik bilgilerini yakalamak güvenilir olmayan bir derleme için teknik olarak mümkündür. Bu durumu önlemek için Güvenlik gereksinimleriniz varsa, aşağıdaki tekniklerden birini kullanarak, hedeflenen XAML ad alanı eşlemesi yapılmalıdır:  
  
- Uygulamanızın XAML tarafından yapılan tüm XAML ad alanı eşlemesi içindeki tanımlayıcı adı ile tam derleme adını kullanın.  
  
- Başvuru bütünleştirilmiş kodları, sabit bir kümesi için belirli bir oluşturarak eşleme derleme kısıtlama <xref:System.Xaml.XamlSchemaContext> okuyucular ve XAML yazarları, XAML için nesne. Bkz. <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>XAML tür eşlemesi ve tür sistem erişimi  
 XAML için CLR temel CLR tür sistemine nasıl uyguladığını eşdüzeyde, birçok yönden kendi tür sistemi destekler. Ancak, bazı yönlerini türü tanıma burada kendi tür bilgilerini temel alarak bir türle ilgili güven kararları yapmak için türlerini destekleyen CLR türü bilgileri erteleme. XAML tür sistemi belirli raporlama özelliklerinin bazıları sanal yöntemler açık kalır ve bu nedenle, tam olarak özgün .NET Framework XAML hizmetlerinde uygulamaları denetimi altında olmayan olmasıdır. XAML tür sistemi genişletilebilirliği, XAML kendisi ve olası alternatif tür eşlemesi stratejileri varsayılan XAML şema içeriği ve varsayılan CLR destekli uygulama karşı eşleşecek şekilde genişletilebilir olduğundan bu genişletilebilirlik noktaları vardır. Daha fazla bilgi için bkz özgü Notlar çeşitli özelliklerini <xref:System.Xaml.XamlType> ve <xref:System.Xaml.XamlMember>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xaml.Permissions.XamlAccessLevel>
