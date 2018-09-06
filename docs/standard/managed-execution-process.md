---
title: Yönetilen Yürütme İşlemi
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- source code language
- code, managed execution process
- runtime, managed execution process
- compiling source code, managed execution process
- managed execution process
- common language runtime, managed execution process
ms.assetid: 476b03dc-2b12-49a7-b067-41caeaa2f533
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33c498e8379d68287bfe4a2e781d6797fd6b4c10
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870998"
---
# <a name="managed-execution-process"></a>Yönetilen Yürütme İşlemi
<a name="introduction"></a> Yönetilen yürütme işlemi, bu konunun ilerleyen bölümlerinde ayrıntılı ele alınmıştır aşağıdaki adımları içerir:  
  
1.  [Bir derleyici seçme](#choosing_a_compiler).  
  
     Ortak dil çalışma zamanı tarafından sağlanan avantajlar elde etmek için çalışma zamanını hedefleyen bir veya daha fazla dil derleyicileri kullanmanız gerekir.  
  
2.  [MSIL kodunuzu derlerken](#compiling_to_msil).  
  
     Derleme, kaynak kodunuzu Microsoft Ara diline (MSIL) çevirir ve gerekli meta veriler oluşturur.  
  
3.  [Yerel kod için MSIL derleme](#compiling_msil_to_native_code).  
  
     Yürütme sırasında just-ın-time (JIT) derleyici MSIL'yi yerel kod içine çevirir. Bu derleme sırasında kod MSIL ve meta verileri olup olmadığını kod tür bakımından güvenli olacak şekilde belirlenebilir kullanıma bulmak için bir doğrulama işlemi geçmesi gerekir.  
  
4.  [Kod çalıştırma](#running_code).  
  
     Ortak dil çalışma zamanı yürütme bağlantısı ve yürütme sırasında kullanılabilecek hizmetleri sağlayan altyapıyı sağlar.  
  
<a name="choosing_a_compiler"></a>   
## <a name="choosing-a-compiler"></a>Bir derleme seçme  
 Ortak dil çalışma (CLR) tarafından sağlanan avantajlar elde etmek için Visual Basic, C#, Visual C++, F # veya bir Eiffel, Perl veya COBOL derleyici gibi çok sayıda üçüncü taraf derleyicileri biri gibi çalışma zamanını hedefleyen bir veya daha fazla dil derleyicileri kullanmanız gerekir.  
  
 Çok dilli yürütme ortamı olduğundan, çalışma zamanının çok çeşitli veri türleri ve dil özelliklerini destekler. Bu özellikleri kullanarak kodunuzun tasarlarken ve hangi çalışma zamanı özellikleri kullanılabilir kullandığınız dil derleyicisi belirler. Derleyici, çalışma zamanı değil, kodunuzu kullanmalısınız sözdizimi oluşturur. Bileşeniniz diğer dillerde yazılmış bileşenler tarafından tamamen kullanılabilir olması gerekiyorsa, bileşeninizin dışarı aktarılan türler dahil olan dil özellikleri açığa çıkarmalıdır [dil bağımsızlığı ve dilden bağımsız bileşenler](../../docs/standard/language-independence-and-language-independent-components.md) (CLS). Kullanabileceğiniz <xref:System.CLSCompliantAttribute> kodunuzu CLS uyumlu olduğundan emin olmak için özniteliği. Daha fazla bilgi için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../docs/standard/language-independence-and-language-independent-components.md).  
  
 [Başa dön](#introduction)  
  
<a name="compiling_to_msil"></a>   
## <a name="compiling-to-msil"></a>MSIL olarak derleme  
 Yönetilen kod için derleme, derleyici kaynak kodunuzu yerel kod için verimli bir şekilde dönüştürülebilen talimatları CPU bağımsız kümesi olan Microsoft Ara dilini (MSIL) dönüştürecektir. MSIL yönergeleri yüklenirken, depolama, başlatma ve nesneler üzerinde çağıran yöntemleri için yanı sıra, aritmetik ve mantıksal işlemler, denetim akışı, doğrudan bellek erişimi, özel durum işleme ve diğer işlemler için yönergeler içerir. Kod çalıştırılmasından önce MSIL CPU'ya özel kod, genellikle göre dönüştürülmelidir bir [just-in-time (JIT) derleyici](#compiling_msil_to_native_code). Ortak dil çalışma zamanının desteklediği her bilgisayar mimarisi için bir veya daha fazla JIT derleyiciler sağlar çünkü JIT olarak derlenmiş ve çalışma MSIL aynı dizi desteklenen her mimari üzerinde olabilir.  
  
 MSIL derleyici üretir, meta verileri de oluşturur. Meta veriler dahil her tür tanımı, her türün üyeleri, kodunuzu başvuran üyeleri ve yürütme sırasında çalışma zamanı kullanan diğer veri imzalarını kodunuzdaki türleri açıklanmaktadır. MSIL ve meta veriler, temel alır ve yayımlanan Microsoft PE ve geçmişe yönelik olarak yürütülebilir içerik için kullanılan ortak nesne dosyası biçimi (COFF) genişleten bir taşınabilir yürütülebilir (PE) dosyası içinde yer alır. Meta veri yanı sıra MSIL veya yerel kod modeli sağlar, bu dosya biçimi, ortak dil çalışma zamanı görüntüleri tanımak işletim sistemi sağlar. Meta veri MSIL birlikte dosyasındaki varlığını, kodun kendisini tanımlamak tür kitaplıkları veya arabirim tanımlama dili (IDL) gerek yoktur anlamına gelen sağlar. Çalışma zamanı bulur ve yürütme sırasında gerektiği şekilde dosyasından meta verileri ayıklar.  
  
 [Başa dön](#introduction)  
  
<a name="compiling_msil_to_native_code"></a>   
## <a name="compiling-msil-to-native-code"></a>MSIL olarak yerel kod derleme  
 Microsoft Ara dilini (MSIL) çalıştırmadan önce hedef makine mimarisi için yerel kod için ortak dil çalışma zamanı karşı derlenmelidir. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Bu dönüşümü gerçekleştirmek için iki yol sunar:  
  
-   .NET Framework just-in-time (JIT) derleyicisi.  
  
-   .NET Framework [Ngen.exe (yerel Görüntü Oluşturucu)](../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="compilation-by-the-jit-compiler"></a>Derleme için JIT derleyicisi tarafından  
 JIT derlemesi yerel kod isteğe bağlı olarak uygulama çalışma zamanı, bir derlemenin içeriğini ne zaman yüklendi ve yürütülen MSIL dönüştürür. Geliştiriciler, JIT Derleyici her desteklenen CPU mimarisine yönelik ortak dil çalışma zamanı sağlar çünkü JIT olarak derlenmiş olan ve başka bir makine mimariler ile farklı bilgisayarlarda çalışan olabilir bir MSIL derleme kümesi oluşturabilir. Bununla birlikte, yönetilen kod, platforma özgü yerel API'lerin veya platforma özel sınıf kitaplığı çağırırsa, yalnızca bu işletim sisteminde çalışır.  
  
 JIT derlemesi bazı kod yürütülmesi sırasında hiçbir zaman çağrılabilir olasılığını dikkate alır. Bir PE dosyasında tüm MSIL yerel koda dönüştürmek için süresi ve bellek kullanarak yerine, MSIL yürütme sırasında gerektiği şekilde dönüştürür ve elde edilen yerel kod, bellekte saklar, böylece işlem bağlamında sonraki çağrılar için erişilebilir. Yükleyici oluşturur ve türü yüklü ve başlatılmış bir saplama türü her bir yöntemin ekler. Yöntemi ilk kez çağrıldığında saplama denetim MSIL bu yöntem için yerel kod içine dönüştürür ve saplama doğrudan üretilen yerel kod işaret edecek şekilde değiştirir ve JIT derleyicisi geçer. Bu nedenle, JIT olarak derlenmiş bir Metoda yapılan sonraki çağrılar, doğrudan yerel koda gidin.  
  
### <a name="install-time-code-generation-using-ngenexe"></a>NGen.exe kullanarak yükleme zamanı kodu oluşturma  
 Çünkü JIT derleyicisine, yerel kod için tek tek zaman bir derlemenin MSIL dönüştürür, derlemede tanımlanan bir yöntem de çağrıldığında, çalışma zamanında olumsuz performansını etkiler. Azaltılmış performansın kabul edilebilir olduğunu çoğu durumda. Daha da önemlisi, JIT derleyicisi tarafından üretilen kod derlemesini tetikleyen işleme bağlıdır. Birden çok süreçler arasında paylaşılamaz. Oluşturulan kod veya derleme kümesi paylaşan birden çok işlem farklı bir uygulama birden çok çağrıları arasında paylaşılacak izin vermek için ortak dil çalışma zamanı, zamanında tamamlanan derleme modu destekler. Bu, zaman tamamlanan derleme modu kullanan [Ngen.exe (yerel Görüntü Oluşturucu)](../../docs/framework/tools/ngen-exe-native-image-generator.md) JIT derleyicisi gibi MSIL dönüştürmek için yerel derlemelere çok kod. Ancak, Ngen.exe işlemi üç yolla JIT derleyicisi verilerinden farklılık gösterir:  
  
-   Bu uygulama çalışırken yerine uygulamayı çalıştırmadan önce yerel koda dönüştürme MSIL işlemi gerçekleştirir.  
  
-   Bu, tüm derleme birer birer birer birer bir yöntem yerine derler.  
  
-   Oluşturulan kodun yerel görüntü önbelleğinde disk üzerinde bir dosya olarak kalıcıdır.  
  
### <a name="code-verification"></a>Kod doğrulama  
 Yönetici doğrulamayı atlama kodu izin veren bir güvenlik ilkesi kurmuştur sürece yerel kod için derlemenin bir parçası olarak, doğrulama sürecini MSIL kodu geçmesi gerekir. Doğrulama kodu erişmek için yetkili bellek konumlarına erişir anlamına gelen tür güvenli olup olmadığını öğrenmek için MSIL ve meta verileri inceler. Tür güvenliği nesneleri birbirinden yalıtmaya yardımcı olur ve bunları yanlışlıkla veya kötü amaçlı bozulmaya karşı korunmasına yardımcı olur. Ayrıca, kod üzerinde güvenlik kısıtlamaları güvenilir bir şekilde zorunlu tutulabilir güvence sağlar.  
  
 Çalışma zamanı doğrulanabilir şekilde güvenli yazın olan kod için aşağıdaki deyimleri doğruysa olgu kullanır:  
  
-   Bir başvuru türü kesin olarak başvurulan türü ile uyumludur.  
  
-   Yalnızca uygun şekilde tanımlanmış işlemleri, bir nesne üzerinde çağrılır.  
  
-   Ne iddia Kimlikleridir.  
  
 Doğrulama işlemi sırasında MSIL kodu kod bellek konumlarına erişim ve düzgün bir şekilde tanımlanmış türler yalnızca yoluyla yöntemleri çağırmak onaylayın girişimi incelenir. Örneğin, kod, bir nesnenin alanlarını bellek konumları taşmasına izin veren bir şekilde erişilmesini izin veremez. Ayrıca, doğrulama kodu yanlış MSIL tür güvenliği kurallarını ihlal için neden olabileceği için MSIL doğru bir şekilde oluşturuldu olup olmadığını, belirlemek için inceler. Doğrulama işlemi, tür kullanımı uyumlu kod iyi tanımlanmış bir dizi geçirir ve tür kullanımı uyumlu kod geçirir. Ancak, bazı tür kullanımı uyumlu kod doğrulama doğrulama işleminin bazı sınırlamalar nedeniyle geçebilir değildir ve bazı diller, tasarım gereği, doğrulanabilir şekilde tür kullanımı uyumlu kod üretmez. Kodu çalıştırdığınızda, tür kullanımı uyumlu kod güvenlik ilkesi tarafından gereklidir, ancak doğrulama kodu geçmez, bir özel durum oluşturulur.  
  
 [Başa dön](#introduction)  
  
<a name="running_code"></a>   
## <a name="running-code"></a>Çalışan kod  
 Ortak dil çalışma zamanı, yönetilen yürütme gerçekleşmesi etkinleştirir ve hizmetleri altyapısı yürütme sırasında kullanılabilir sağlar. Bir yöntem çalıştırılmadan önce işlemciye özgü kodu derlenmelidir. Bu ilk kez çağrılır ve ardından çalıştırın JIT olarak derlenmiş MSIL oluşturulan her yöntemi. Yöntem bir sonraki çalıştırıldığında mevcut JIT olarak derlenmiş yerel kod çalıştırılır. Yürütme işlemi tamamlanana kadar JIT derleme ve daha sonra kodu çalıştıran işlem tekrarlanır.  
  
 Yürütme sırasında yönetilen kod gibi hizmetler çöp toplama, güvenlik, yönetilmeyen kod, diller arası hata ayıklama desteği ve geliştirilmiş dağıtım ve sürüm oluşturma desteği ile birlikte çalışabilirlik alır.  
  
 Microsoft [!INCLUDE[winxp](../../includes/winxp-md.md)] ve [!INCLUDE[windowsver](../../includes/windowsver-md.md)], işletim sistemi yükleyicisi COFF üst bilgisinde bir bit inceleyerek yönetilen modüller için denetler. Bit kümesi yönetilen bir modül gösterir. Yükleyici yönetilen modülleri algılarsa, mscoree.dll, yükler ve `_CorValidateImage` ve `_CorImageUnloading` yönetilen modül görüntüleri yüklenmiş ve yüklenmemiş yükleyicisi bildirir. `_CorValidateImage` Aşağıdaki eylemleri gerçekleştirir:  
  
1.  Kod geçerli yönetilen kod olmasını sağlar.  
  
2.  Çalışma zamanında bir giriş noktası için giriş noktası görüntüde değiştirir.  
  
 64 bit Windows üzerinde `_CorValidateImage` bellekte PE32 je typu PE32 + biçimine dönüştürerek görüntü değiştirir.  
  
 [Başa dön](#introduction)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel bakış](../../docs/framework/get-started/overview.md)  
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../docs/standard/language-independence-and-language-independent-components.md)  
- [Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../docs/standard/metadata-and-self-describing-components.md)  
- [Ilasm.exe (IL Derleyici)](../../docs/framework/tools/ilasm-exe-il-assembler.md)  
- [Güvenlik](../../docs/standard/security/index.md)  
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../docs/framework/interop/index.md)  
- [Dağıtım](../../docs/framework/deployment/net-framework-applications.md)  
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
- [Uygulama Etki Alanları](../../docs/framework/app-domains/application-domains.md)
