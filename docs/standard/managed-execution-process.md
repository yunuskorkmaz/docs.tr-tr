---
title: "Yönetilen Yürütme İşlemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source code language
- code, managed execution process
- runtime, managed execution process
- compiling source code, managed execution process
- managed execution process
- common language runtime, managed execution process
ms.assetid: 476b03dc-2b12-49a7-b067-41caeaa2f533
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 702ed3e73117fe01769ec9d7bf939ae8df523793
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="managed-execution-process"></a>Yönetilen Yürütme İşlemi
<a name="introduction"></a>Yönetilen yürütme işlemi, bu konunun ilerleyen bölümlerinde ayrıntılı olarak ele alınmıştır aşağıdaki adımları içerir:  
  
1.  [Derleyici seçme](#choosing_a_compiler).  
  
     Ortak dil çalışma zamanı tarafından sağlanan avantajları elde etmek için çalışma zamanı hedefleyen bir veya daha fazla dil derleyicileri kullanmanız gerekir.  
  
2.  [MSIL kodunuzu derlerken](#compiling_to_msil).  
  
     Derleme kaynak kodunuzu Microsoft Ara dile (MSIL) çevirir ve gerekli meta veriler oluşturur.  
  
3.  [MSIL için yerel kodu derleme](#compiling_msil_to_native_code).  
  
     Yürütme sırasında bir tam zamanında (JIT) derleyici MSIL yerel kod içine çevirir. Bu derleme sırasında kod olup olmadığını kodu türü güvenli belirlenebilir çıkışı bulmak için MSIL ve meta veri inceler bir doğrulama işlemi geçmesi gerekir.  
  
4.  [Kod çalıştırmasını](#running_code).  
  
     Ortak dil çalışma zamanı yerinde ve yürütme sırasında kullanılan hizmetleri yapılacak yürütme etkinleştirir altyapı sağlar.  
  
<a name="choosing_a_compiler"></a>   
## <a name="choosing-a-compiler"></a>Bir derleme seçme  
 Ortak dil çalışma zamanı tarafından (CLR) sağlanan avantajları elde etmek için bir veya daha fazla dil derleyicileri hedefleyen Visual Basic, C#, Visual C++, F # veya Eiffel, Perl veya COBOL derleyici gibi çok sayıda üçüncü taraf derleyicileri biri gibi çalışma zamanı kullanmanız gerekir.  
  
 Çok dilli yürütme ortamı olduğu için çalışma zamanı çok çeşitli veri türleri ve dil özellikleri destekler. Kullandığınız dil derleyici hangi çalışma zamanı özelliklerin kullanılabilir olduğunu belirler ve bu özellikleri kullanarak kodunuzu tasarlayın. Derleyici, çalışma zamanı değil, kodunuzu kullanmalısınız sözdizimi oluşturur. Bileşeniniz diğer dillerde yazılmış bileşenler tarafından tamamen kullanılabilir olması gerekiyorsa, bileşenin verilen türleri dahil edilen dil özellikleri kullanıma [dil bağımsızlığı ve dilden bağımsız bileşenler](../../docs/standard/language-independence-and-language-independent-components.md) (CLS). Kullanabileceğiniz <xref:System.CLSCompliantAttribute> özniteliği kodunuzu CLS ile uyumlu olduğundan emin olun. Daha fazla bilgi için bkz: [dil bağımsızlığı ve dilden bağımsız bileşenler](../../docs/standard/language-independence-and-language-independent-components.md).  
  
 [Başa dön](#introduction)  
  
<a name="compiling_to_msil"></a>   
## <a name="compiling-to-msil"></a>MSIL için derleme  
 Yönetilen kod için derleme, derleyici, kaynak kodunuzu yerel koda verimli bir şekilde dönüştürülebilir yönergeler CPU bağımsız kümesi olan Microsoft Ara dili (MSIL) çevirir. MSIL yüklenirken, depolama, başlatma ve nesneler üzerinde çağıran yöntemleri için yönergeler yanı sıra, aritmetik ve mantıksal işlemleri, akış denetimi, doğrudan bellek erişimi, özel durum işleme ve diğer işlemler için yönergeler içerir. Kod çalıştırmadan önce MSIL CPU'ya özel kod, genellikle göre dönüştürülmelidir bir [tam zamanında (JIT) derleyici](#compiling_msil_to_native_code). Ortak dil çalışma zamanı desteklediği her bilgisayar mimarisi için bir veya daha fazla JIT derleyicileri sağladığı için MSIL aynı kümesini JIT derlenmiş ve çalışma desteklenen tüm mimarisine olabilir.  
  
 MSIL derleyici ürettiği zaman ayrıca meta veriler üretir. Meta veri türleri dahil her tür tanımı, her tür üyeleri, kodunuzu başvuran üyeleri ve çalışma zamanı yürütme sırasında kullanan diğer veri imzalarını kodunuzda açıklar. MSIL ve meta veri dosyasında, temel alır ve geçmişte yürütülebilir içerik için kullanılan ortak nesne dosyası biçimi (COFF) ve yayımlanan Microsoft PE genişleten bir taşınabilir yürütülebilir (PE) bulunur. Meta veri yanı sıra MSIL veya yerel kod düzenler, bu dosya biçimi ortak dil çalışma zamanı görüntüleri tanımak işletim sisteminin sağlar. MSIL birlikte dosyasındaki meta veri varlığını hangi tür kitaplığı veya arabirimi tanım dili (IDL) için gerekli olduğu anlamına gelir kendisini tanımlamak kodunuzu sağlar. Çalışma zamanı bulur ve yürütme sırasında gerektiği gibi meta veri dosyasından ayıklar.  
  
 [Başa dön](#introduction)  
  
<a name="compiling_msil_to_native_code"></a>   
## <a name="compiling-msil-to-native-code"></a>MSIL yerel kodu derleme  
 Microsoft Ara dili (MSIL) çalıştırmadan önce karşı ortak dil çalışma zamanı hedef makine mimarisi için yerel koda derlenmiş gerekir. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Bu dönüştürme gerçekleştirmek için iki yöntem sunar:  
  
-   .NET Framework tam zamanında (JIT) derleyicisi.  
  
-   .NET Framework [Ngen.exe (yerel Görüntü Oluşturucu)](../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="compilation-by-the-jit-compiler"></a>JIT Derleyici tarafından derleme  
 JIT derleme MSIL uygulama çalışma zamanı bütünleştirilmiş içeriğini ne zaman yüklendi ve yürütülen isteğe bağlı yerel koda dönüştürür. Ortak dil çalışma zamanı JIT Derleyici desteklenen her CPU mimarisi için sağladığı olduğundan, geliştiriciler JIT derlenmiş ve farklı bilgisayarlarda farklı makine mimarileri ile çalışma MSIL derlemeler kümesini oluşturabilir. Bununla birlikte, yönetilen kod platforma özgü yerel API'leri veya bir platforma özgü sınıf kitaplığı çağırırsa, yalnızca bu işletim sisteminde çalışır.  
  
 JIT derleme bazı kod hiç yürütme sırasında çağrılabilir olasılığını dikkate alır. Yerine süresi ve bellek PE dosyasındaki tüm MSIL yerel koda dönüştürmek için onu MSIL yürütme sırasında gerektiği şekilde dönüştürür ve böylece bu işlemin bağlamında sonraki çağrılar için erişilebilir elde edilen yerel kod bellekte depolar. Yükleyici oluşturur ve türü yüklenmiş ve başlatılmış bir saplama bir türdeki her yöntem ekler. Bir yöntem ilk kez çağrıldığında, saplama denetim bu yöntem için MSIL yerel koda dönüştürür ve doğrudan oluşturulan yerel kod işaret edecek şekilde saplama değiştirir JIT Derleyici geçirir. Bu nedenle, JIT derlenmiş yöntemine yapılan sonraki çağrılar doğrudan yerel koda gitme olanağı.  
  
### <a name="install-time-code-generation-using-ngenexe"></a>NGen.exe kullanarak yükleme zamanı kodu oluşturma  
 Çünkü yerel kod tek tek zaman bir derlemenin MSIL JIT Derleyici dönüştürür bu derlemede tanımlanan yöntemler olarak adlandırılır, çalışma zamanında olumsuz performansı etkiler. Düşüklüğü, artan performans kabul edilebilir çoğu durumda. Daha da önemlisi, JIT Derleyici tarafından üretilen kod derleme tetiklenen işleme bağlıdır. Birden çok süreçler arasında paylaşılamaz. Bir uygulamanın birden çok çağrılarını arasında veya derlemeler kümesini paylaşan birden çok işlemler arasında paylaşılması için oluşturulan kodu izin vermek için ortak dil çalışma zamanı, zaman önceden derleme moduna destekler. Bu, zaman önceden derleme moduna kullanan [Ngen.exe (yerel Görüntü Oluşturucu)](../../docs/framework/tools/ngen-exe-native-image-generator.md) JIT Derleyici yaptığı gibi MSIL dönüştürmek için yerel derlemelere çok kod. Ancak, Ngen.exe işlemi, üç yolla JIT Derleyici farklıdır:  
  
-   Uygulama çalışırken yerine uygulamayı çalıştırmadan önce yerel koda dönüştürme MSIL işlemini gerçekleştirir.  
  
-   Tüm bütünleştirilmiş birer birer birer birer bir yöntem yerine derler.  
  
-   Bu oluşturulan kodda yerel görüntü önbelleği disk üzerindeki bir dosya olarak devam ettirir.  
  
### <a name="code-verification"></a>Kod doğrulama  
 Bir yönetici doğrulamayı atlama kodu izin veren bir güvenlik ilkesi kurulduğunda sürece yerel koda kendi derleme bir parçası olarak, bir doğrulama işlemi MSIL kod geçmesi gerekir. Doğrulama MSIL ve meta verileri kodu erişimi için yetkilendirilmiş bellek konumlarına erişen anlamı türü güvenli olup olmadığını öğrenmek için inceler. Tür güvenliği nesneleri birbirinden yalıtmak yardımcı olur ve yanlışlıkla veya kötü amaçlı bozulmaya karşı korunmasına yardımcı olur. Ayrıca, kod üzerinde güvenlik kısıtlamaları güvenilir bir şekilde zorunlu tutulabilir güvence sağlar.  
  
 Çalışma zamanı aşağıdaki deyimleri için doğrulanabilir şekilde güvenli türü olan kodu doğru olgu kullanır:  
  
-   Türüne bir başvuru kesinlikle başvurulan türü ile uyumludur.  
  
-   Yalnızca uygun şekilde tanımlanan işlemlerine bir nesne üzerinde çağrılır.  
  
-   Bunlar olması talep hesaplardır.  
  
 Doğrulama işlemi sırasında kod bellek konumlarına erişmek ve düzgün şekilde tanımlı türler yalnızca yoluyla yöntemlerini çağıran onaylayın girişimi MSIL kod incelenir. Örneğin, kod taşmasına belleğinden izin veren bir şekilde Erişilecek nesnenin alanları izin veremez. Ayrıca, doğrulama kodu yanlış MSIL türü güvenlik kuralları ihlali için yol açabileceğinden MSIL doğru bir şekilde oluşturuldu olup olmadığını, belirlemek için inceler. Tür kullanımı uyumlu kod iyi tanımlanmış bir dizi doğrulama işlemi başarılı ve güvenli bir türe sahip code geçirir. Ancak, bazı tür kullanımı uyumlu kod doğrulama doğrulama işlemi bazı sınırlamaları nedeniyle geçebilir değildir ve bazı dillerde tasarım gereği, doğrulanabilir şekilde tür kullanımı uyumlu kod üretmez. Tür kullanımı uyumlu kod güvenlik ilkesi tarafından gerekli ancak kod doğrulama değerine geçmiyor kodu çalıştırdığınızda özel durum oluşur.  
  
 [Başa dön](#introduction)  
  
<a name="running_code"></a>   
## <a name="running-code"></a>Çalışan kod  
 Ortak dil çalışma zamanı yürütme sırasında yönetilen yürütme gerçekleşmesi için hizmetleri altyapısı kullanılabilir sağlar. Bir yöntem çalıştırmadan önce işlemci özgü kod derlenmiş gerekir. Bu olduğunda ilk kez çağrılır ve ardından çalıştırın MSIL oluşturulan her JIT derlenmiş yöntemidir. Yöntemi, İleri çalıştırıldığında mevcut JIT derlenmiş yerel kod çalıştırılır. JIT derleme ve kodu çalıştırma işlemi, yürütme işlemi tamamlanana kadar yinelenir.  
  
 Yürütme sırasında yönetilen kod atık toplama, güvenlik, yönetilmeyen kod, çapraz dil hata ayıklama desteği ve Gelişmiş dağıtıma ve sürüm oluşturma desteği ile birlikte çalışabilirlik gibi hizmetleri alır.  
  
 Microsoft [!INCLUDE[winxp](../../includes/winxp-md.md)] ve [!INCLUDE[windowsver](../../includes/windowsver-md.md)], işletim sistemi yükleyicisi biraz COFF üstbilgisinde inceleyerek yönetilen modülleri için denetler. Ayarlanan bit yönetilen bir modül gösterir. Yükleyici yönetilen modüller algılarsa, mscoree.dll, yükler ve `_CorValidateImage` ve `_CorImageUnloading` yönetilen modül görüntüleri yüklendiğinde ve kaldırıldığında olduğunda yükleyicisi bildirin. `_CorValidateImage`Aşağıdaki eylemleri gerçekleştirir:  
  
1.  Kod geçerli yönetilen kod olmasını sağlar.  
  
2.  Çalışma zamanında bir giriş noktası için giriş noktası görüntüdeki değiştirir.  
  
 64-bit Windows `_CorValidateImage` PE32 + biçimine PE32 dönüştürerek bellekte görüntüsü değiştirir.  
  
 [Başa dön](#introduction)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel bakış](../../docs/framework/get-started/overview.md)  
 [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../docs/standard/language-independence-and-language-independent-components.md)  
 [Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../docs/standard/metadata-and-self-describing-components.md)  
 [Ilasm.exe (IL Derleyici)](../../docs/framework/tools/ilasm-exe-il-assembler.md)  
 [Güvenlik](../../docs/standard/security/index.md)  
 [Yönetilmeyen Kod ile Birlikte Çalışma](../../docs/framework/interop/index.md)  
 [Dağıtım](../../docs/framework/deployment/net-framework-applications.md)  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Uygulama Etki Alanları](../../docs/framework/app-domains/application-domains.md)
