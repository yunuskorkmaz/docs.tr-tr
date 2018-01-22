---
title: "Ortak Dil Çalışma Zamanı (CLR)"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET Framework, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4aa9a6d37a52d5f15643e9179060450a2d7a34c4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="common-language-runtime-clr"></a>Ortak Dil Çalışma Zamanı (CLR)
.NET Framework kod çalışır ve geliştirme sürecini kolaylaştırmak hizmetleri sağlayan ortak dil çalışma adlı bir çalışma zamanı ortamı sağlar.  
  
 Derleyicileri ve araçları ortak dil çalışma zamanı 's işlevselliği kullanıma sunar ve bu yönetilen yürütme ortamından bu avantajları kod yazmanızı etkinleştirin. Çalışma zamanı hedefleyen bir dil derleyici geliştirmek kod yönetilen kod çağrılır; diller arası tümleştirme, diller arası özel durum işleme, Gelişmiş güvenlik, sürüm ve dağıtım desteği bileşen etkileşimi ve hata ayıklama ve profil oluşturma hizmetleri için basitleştirilmiş bir model gibi özelliklerinden yararlanır.  
  
> [!NOTE]
>  Derleyicileri ve araçları tür sistemi, meta veri biçimi ve çalışma zamanı ortamı (sanal yürütme sistemi) tüm, ECMA ortak dil gibi ortak bir standart tanımlı olduğundan, ortak dil çalışma zamanı tüketebileceği bir çıktı oluşturmak için Altyapı belirtimi. Daha fazla bilgi için bkz: [ECMA C# ve ortak dil altyapısı belirtimleri](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/).  
  
 Yönetilen kod hizmetleri sağlamak üzere çalışma zamanı etkinleştirmek için dil derleyicileri türleri, üyeleri ve kodunuzu başvurularında açıklayan meta veriler yayması gerekir. Meta veriler koduyla depolanır; Her yüklenebilir ortak dil çalışma zamanı taşınabilir yürütülebilir (PE) dosya meta verileri içerir. Çalışma zamanı meta verileri bulun ve sınıfları yük bellek durumlarda yerleştirme yöntemi çağrılarını çözmek yerel kod oluşturmak güvenlik zorlama ve çalışma zamanı bağlam sınırları ayarlamak kullanır.  
  
 Çalışma zamanı otomatik olarak nesne düzenini işler ve artık kullanıldığı sırada serbest nesnelere başvurular yönetir. Bu şekilde, yaşam süresi yönetilen nesneleri yönetilen veri denir. Çöp toplama bellek sızıntıları ve bunun yanı sıra diğer bir ortak programlama hataları ortadan kaldırır. Kodunuzu yönetiliyorsa, .NET Framework uygulamanızda yönetilen veri, yönetilmeyen veri ya da yönetilen ve yönetilmeyen verilerini kullanabilirsiniz. İlkel türler gibi kendi türleri dil derleyicileri tedarik çünkü olabilir her zaman bilmek (veya bilmeniz gerekir), verilerinizi mı yönetiliyor.  
  
 Ortak dil çalışma zamanı tasarım bileşenleri ve nesneleri dillerde etkileşim uygulamalara kolaylaştırır. Farklı dillerde yazılmış nesneleri birbirleri ile iletişim kurabilir ve davranışları sıkı bir şekilde tümleştirilebilir. Örneğin, bir sınıf tanımlama ve özgün sınıfından bir sınıf türetin veya özgün sınıf üzerinde bir yöntemi çağırmak için farklı bir dil kullanın. Sınıfının bir örneği, farklı bir dilde yazılmış bir sınıfın bir yönteme de geçirebilirsiniz. Bu diller arası tümleştirme dil derleyicileri ve çalışma zamanı hedef Araçları çalışma zamanı tarafından tanımlanan bir ortak tür sistemi kullanın ve bunlar zamanının yeni türleri tanımlama yanı sıra oluşturma, kullanma, kalıcı, kurallarına olası nedeni ve türlerine bağlama.  
  
 Bunların meta verilerini bir parçası olarak, tüm yönetilen bileşenleri oluşturuldukları kaynakları ve bileşenleri hakkında bilgi taşır. Çalışma zamanı bileşeni veya uygulama, gereken her şeyi belirtilen sürümleri kodunuzu bazı unmet bağımlılık nedeniyle bölün olasılığı kılan olduğundan emin olmak için bu bilgileri kullanır. Kayıt bilgileri ve durumu verileri artık burada bunlar kurmak ve bakımını zor olabilir kayıt defterinde depolanır. Bunun yerine, tanımladığınız türleri (ve bağımlılıklarını) hakkında bilgi koduyla bileşen çoğaltma ve temizleme görevleri daha az karmaşık hale meta veri depolanır.  
  
 Dil derleyicileri ve araçları çalışma zamanı işlevselliği yararlı ve sezgisel geliştiricilere yönelik yolla kullanıma sunar. Bu, bazı özellikler çalışma zamanının daha belirgin bir ortamında başka olabileceği anlamına gelir. Çalışma zamanı deneyimi nasıl hangi dil derleyicileri veya araçlarını kullanmanız bağlıdır. Örneğin, bir Visual Basic Geliştirici varsa, ortak dil çalışma zamanı ile daha fazla nesne yönelimli özelliği daha önce Visual Basic dili olduğunu fark edebilirsiniz. Çalışma zamanı aşağıdaki avantajları sağlar:  
  
-   Performans iyileştirmeleri.  
  
-   Kolayca bileşenleri kullanma yeteneğini diğer dillerde geliştirmiştir.  
  
-   Sınıf kitaplığı tarafından sağlanan Genişletilebilir türleri.  
  
-   Dil özellikleri devralma, arabirimleri ve nesne odaklı programlama için aşırı yükleme gibi.  
  
-   Birden çok iş parçacıklı ve ölçeklenebilir uygulamaları oluşturulmasını sağlayan açık boş iş parçacığı oluşturma desteği.  
  
-   Yapılandırılmış özel durum işleme için destek.  
  
-   Özel öznitelikler için destek.  
  
-   Çöp toplama.  
  
-   İşlev işaretçileri yerine temsilciler kullanımı artan tür güvenliği ve güvenlik için. Temsilciler hakkında daha fazla bilgi için bkz: [ortak tür sistemi](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="versions-of-the-common-language-runtime"></a>Ortak dil çalışma zamanı sürümleri  
 .NET Framework sürüm numarası içerdiği CLR sürüm numarasını mutlaka karşılık gelmiyor. Aşağıdaki tabloda iki sürüm numaralarının nasıl bağıntısını gösterir.  
  
|.NET Framework sürümü|CLR sürümü içerir|  
|----------------------------|--------------------------|  
|1.0|1.0|  
|1.1|1.1|  
|2,0|2,0|  
|3.0|2,0|  
|3.5|2,0|  
|4|4|  
|4.5 (4.5.1 ve 4.5.2 dahil)|4|  
|4.6 (4.6.1 ve 4.6.2 dahil)|4|
|4.7 (4.7.1 dahil)|4|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Yönetilen Yürütme İşlemi](../../docs/standard/managed-execution-process.md)|Ortak dil çalışma zamanı yararlanmak için gereken adımları açıklar.|  
|[Otomatik Bellek Yönetimi](../../docs/standard/automatic-memory-management.md)|Çöp toplayıcı'nın ayırır ve belleği serbest bırakır nasıl açıklanmaktadır.|  
|[NIB: .NET Framework'ün genel bakış](http://msdn.microsoft.com/library/ea38ac1e-92af-4d1b-8db1-e8a5ea10ed85)|Ortak tür sistemi, diller arası birlikte çalışabilirlik, yönetilen yürütme, uygulama etki alanları ve derlemeler gibi anahtar .NET Framework kavramlarını açıklar.|  
|[Ortak Tür Sistemi](../../docs/standard/base-types/common-type-system.md)|Nasıl türleri bildirilen kullanılan ve çalışma zamanında diller arası tümleştirme desteklemek yönetilen açıklar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sürümler ve Bağımlılıklar](../../docs/framework/migration-guide/versions-and-dependencies.md)
