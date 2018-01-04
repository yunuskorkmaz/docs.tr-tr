---
title: Derleme Bildirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41dc27798e9d39d391e5958b86f691e3a0062582
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-manifest"></a>Derleme Bildirimi
Statik veya dinamik tüm derlemeler, derleme içindeki öğelerin birbirleriyle nasıl ilişkili olduğunu açıklayan bir veri koleksiyonu içerir. Derleme bildirimi, bu derleme metaverilerini içerir. Bir derleme bildirimi, derlemenin sürüm gereksinimlerini ve güvenlik kimliğini belirtmek, derlemenin kapsamını tanımlamak ve kaynaklara, sınıflara yapılan atıfları çözmek için gereken tüm metaverileri içerir. Derleme bildirimi, Microsoft ara dili (MSIL) koduyla bir PE dosyası halinde (bir .exe veya .dll) veya yalnızca derleme bildirimi bilgilerini içeren tek bir PE dosyasında tutulabilir.  
  
 Aşağıdaki görselde, bildirimin saklanabileceği farklı şekilleri gösterilmektedir.  
  
 ![Tek bir &#45; dosya derleme](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")  
Derleme türleri  
  
 İlişkili tek bir dosyaya sahip bir derlemede, tek dosyalı derleme oluşturmak amacıyla bildirim PE dosyasına eklenir. Bağımsız bir bildirim dosyasına veya bildirim derlemesindeki PE dosyalarından birine ekli şekilde bir çoklu dosya derlemesi oluşturabilirsiniz.  
  
 Her derlemenin bildirimi, aşağıdaki işlevleri gerçekleştirir:  
  
-   Derlemeyi oluşturan dosyaları listeler.  
  
-   Derlemenin türlerine ve kaynaklarına yapılan atıfların, tanımlarını ve uygulamalarını içeren dosyalarla nasıl eşleştirildiğini yönetir.  
  
-   Derlemenin bağımlı olduğu diğer derlemeleri listeler.  
  
-   Derlemenin tüketicileri ve derlemenin uygulama ayrıntıları arasında bir yöneltme düzeyi sağlar.  
  
-   Derlemeyi kendini açıklayan hale getirir.  
  
## <a name="assembly-manifest-contents"></a>Derleme Bildirimi İçerikleri  
 Aşağıdaki tabloda, derleme bildiriminde bulunan bilgiler gösterilmektedir. İlk dört öğe—derlemenin adı, sürüm numarası, kültür ve tanımlayıcı ad bilgisi— derlemenin kimliğini oluşturur.  
  
|Bilgiler|Açıklama|  
|-----------------|-----------------|  
|Derleme adı|Derlemenin adını belirten bir metin dizesi.|  
|Sürüm numarası|Bir ana ve alt sürüm numarası ve bir düzeltme ve yapı numarası. Ortak dil çalışma zamanı sürüm ilkesini uygulamak için bu numaraları kullanır.|  
|Kültür|Derlemenin desteklediği kültür veya dil hakkında bilgi. Bu bilgiler, yalnızca bir derlemeyi kültüre veya dile özel bilgi içeren bir uydu derleme olarak tanımlamak için kullanılmalıdır. (Kültür bilgisine sahip bir derleme, otomatik olarak bir uydu derleme kabul edilir.)|  
|Tanımlayıcı ad bilgisi|Derlemeye tanımlayıcı ad verilmişse yayımcıdan gelen ortak anahtar.|  
|Derlemedeki tüm dosyaların listesi|Derlemede bulunan her dosyayla bir dosya adının karması. Derlemeyi oluşturan tüm dosyaların, derleme bildirimini içeren dosyayla aynı dizinde olması gerektiğine dikkat edin.|  
|Tür başvuru bilgisi|Çalışma zamanı tarafından bir tür başvurusu ile bildirimini ve uygulamasını içeren dosyanın eşleştirilmesi için kullanılan bilgiler. Bu, derlemeden dışarı aktarılan türler için kullanılır.|  
|Atıfta bulunulan derlemeler hakkında bilgi|Derleme tarafından statik olarak atıfta bulunulan diğer derlemelerin listesi. Her başvuru, bağımlı derlemenin adını, derleme metaverilerini (sürüm, kültür, işletim sistemi vb.) ve, derleme tanımlayıcı ada sahipse, ortak anahtarı içerir.|  
  
 Kodunuzda derleme öznitelikleri kullanarak derleme bildirimine bazı bilgiler ekleyebilir veya bazı bilgileri değiştirebilirsiniz. Ticari Marka, Telif Hakkı, Ürün, Şirket ve Bilgilendirme Sürümü dahil olmak üzere sürüm bilgilerini ve bilgilendirme özniteliklerini değiştirebilirsiniz. Derleme özniteliklerinin tam bir listesi için bkz: [ayarı derleme özniteliklerinin](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kod İçerikleri](../../../docs/framework/app-domains/assembly-contents.md)  
 [Bütünleştirilmiş Kod Sürümü Oluşturma](../../../docs/framework/app-domains/assembly-versioning.md)  
 [Uydu Derlemeleri Oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)
