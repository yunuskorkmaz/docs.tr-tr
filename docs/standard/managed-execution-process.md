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
ms.openlocfilehash: 46a266849f137076170287aeb10becedf83ccf78
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160228"
---
# <a name="managed-execution-process"></a>Yönetilen Yürütme İşlemi
<a name="introduction"></a>Yönetilen yürütme işlemi, bu konunun ilerleyen bölümlerinde ayrıntılı olarak ele alınan aşağıdaki adımları içerir:  
  
1. [Derleyici seçme](#choosing_a_compiler).  
  
     Ortak dil çalışma zamanı tarafından belirtilen avantajları elde etmek için, çalışma zamanını hedefleyen bir veya daha fazla dil derleyicileri kullanmanız gerekir.  
  
2. [Kodunuzu MSIL 'e derleme](#compiling_to_msil).  
  
     Derleme, kaynak kodunuzu Microsoft ara dili 'ne (MSIL) çevirir ve gerekli meta verileri oluşturur.  
  
3. [MSIL yerel koda derleniyor](#compiling_msil_to_native_code).  
  
     Yürütme zamanında, tam zamanında (JıT) derleyici MSIL 'i yerel koda dönüştürür. Bu derleme sırasında kod, kodun güvenli olarak belirlenip belirlenemediğini öğrenmek için MSIL ve meta verileri inceleyen bir doğrulama işlemi iletmelidir.  
  
4. [Kod çalıştırılıyor](#running_code).  
  
     Ortak dil çalışma zamanı, yürütme sırasında kullanılabilecek yürütme ve Hizmetleri yürütmeye olanak tanıyan altyapıyı sağlar.  
  
<a name="choosing_a_compiler"></a>
## <a name="choosing-a-compiler"></a>Derleyici seçme  
 Ortak dil çalışma zamanı (CLR) tarafından belirtilen avantajları elde etmek için Visual Basic, C#, görsel C++, F#veya bir Eiffel, Perl veya COBOL derleyicisi gibi birçok üçüncü taraf derleyicisinden birini hedefleyen bir veya daha fazla dil derleyicisini kullanmanız gerekir.  
  
 Çok dilli bir yürütme ortamı olduğundan, çalışma zamanı çok çeşitli veri türlerini ve dil özelliklerini destekler. Kullandığınız dil derleyicisi, hangi çalışma zamanı özelliklerinin kullanılabilir olduğunu belirler ve bu özellikleri kullanarak kodunuzu tasarlayamazsınız. Çalışma zamanı değil, kodunuzun kullanması gereken söz dizimini belirler. Bileşeninizin diğer dillerde yazılmış bileşenler tarafından tamamen kullanılabilir olması gerekiyorsa, bileşeninizin verilme türleri yalnızca [Dil bağımsızlığı ve dilden bağımsız bileşenlere](../../docs/standard/language-independence-and-language-independent-components.md) (CLS) dahil olan dil özelliklerini kullanıma sunmalıdır. Kodunuzun CLS uyumlu olduğundan emin olmak için <xref:System.CLSCompliantAttribute> özniteliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../docs/standard/language-independence-and-language-independent-components.md).  
  
 [Başa dön](#introduction)  
  
<a name="compiling_to_msil"></a>
## <a name="compiling-to-msil"></a>MSIL 'e derleme  
 Yönetilen koda derlerken, derleyici kaynak kodunuzu Microsoft ara dili 'ne (MSIL) çevirir ve bu, yerel koda etkin bir şekilde dönüştürülebilecek bir CPU bağımsız yönerge kümesidir. MSIL, nesneler üzerinde Yöntem yükleme, depolama, başlatma ve çağırma yönergelerini, ayrıca aritmetik ve mantıksal işlemler, denetim akışı, doğrudan bellek erişimi, özel durum işleme ve diğer işlemler için yönergeler içerir. Kod çalıştırılmadan önce, MSIL 'nin genellikle [tam zamanında (JIT) derleyicisi](#compiling_msil_to_native_code)tarafından, CPU 'ya özgü koda dönüştürülmesi gerekir. Ortak dil çalışma zamanı, desteklediği her bilgisayar mimarisi için bir veya daha fazla JıT derleyicisi sağladığından, aynı MSIL kümesi JıT derlenebilir ve desteklenen herhangi bir mimaride çalıştırılabilir.  
  
 Bir derleyici MSIL ürettiğini de meta veriler üretir. Meta veriler, her türün tanımı, her bir türün üyesi, kodunuzun başvurduğu Üyeler ve çalışma zamanının yürütme sırasında kullandığı diğer veriler de dahil olmak üzere kodunuzdaki türleri açıklar. MSIL ve meta veriler, bir Taşınabilir çalıştırılabilir (PE) dosyasında bulunur ve bu, yüklenen Microsoft PE ve ortak nesne dosyası biçimi (COFF) tarafından yürütülebilir içerik için kullanılmaktadır. MSIL veya yerel kod ile meta verilerin yanı sıra bu dosya biçimi, işletim sisteminin ortak dil çalışma zamanı görüntülerini tanımasını sağlar. Dosyadaki meta verilerin MSIL ile birlikte bulunması, kodunuzun kendisini tanımlamasını sağlar, bu da tür kitaplıkları veya arabirim tanımlama dili (IDL) için gerekli değildir. Çalışma zamanı, yürütme sırasında gerekli olduğu gibi dosyadaki meta verileri bulur ve ayıklar.  
  
 [Başa dön](#introduction)  
  
<a name="compiling_msil_to_native_code"></a>
## <a name="compiling-msil-to-native-code"></a>MSIL 'i yerel koda derleme  
 Microsoft ara dili 'ni (MSIL) çalıştırabilmeniz için önce, hedef makine mimarisi için ortak dil çalışma zamanına göre yerel koda derlenmesi gerekir. .NET Framework, bu dönüştürmeyi gerçekleştirmek için iki yol sunar:  
  
- .NET Framework Just-In-Time (JıT) derleyicisi.  
  
- .NET Framework [Ngen. exe (yerel görüntü Oluşturucu)](../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="compilation-by-the-jit-compiler"></a>JıT derleyicisi tarafından derleme  
 JıT derlemesi, bir derlemenin içeriği yüklenip yürütüldüğünde, uygulama çalışma zamanında MSIL 'i yerel koda dönüştürür. Ortak dil çalışma zamanı desteklenen her bir CPU mimarisi için bir JıT derleyicisi sağladığından, geliştiriciler JıT derlenebilecek ve farklı makine mimarilerine sahip farklı bilgisayarlarda çalıştırılabilen bir MSIL derlemeleri kümesi oluşturabilir. Ancak, yönetilen kodunuz platforma özgü yerel API 'Leri veya platforma özgü bir sınıf kitaplığını çağırırsa, yalnızca o işletim sisteminde çalışır.  
  
 JıT derlemesi, bazı kodların yürütme sırasında hiçbir zaman çağrılmaması olasılığını dikkate alır. Bir PE dosyasındaki tüm MSIL 'yi yerel koda dönüştürmek için zaman ve bellek kullanmak yerine, yürütme sırasında MSIL 'yi dönüştürür ve sonuçta elde edilen yerel kodu belleğe depolayarak bu işlem bağlamındaki sonraki çağrılar için erişilebilir olur. Yükleyici, türü yüklenip başlatıldığında bir tür içinde her bir yönteme bir saplama oluşturur ve ekler. Bir yöntem ilk kez çağrıldığında, saplama denetimi JıT derleyicisine geçirir ve bu yöntem için MSIL 'i yerel koda dönüştürür ve saplama, doğrudan oluşturulan yerel koda işaret etmek üzere değişiklik yapar. Bu nedenle, JıT ile derlenen yönteme yapılan sonraki çağrılar doğrudan yerel koda gider.  
  
### <a name="install-time-code-generation-using-ngenexe"></a>NGen. exe kullanarak Install-Time kod üretimi  
 JıT derleyicisi, bu derlemede tanımlanan tek tek Yöntemler çağrıldığında bir derlemenin MSIL 'sini yerel koda dönüştürdüğünden, çalışma zamanında performansı olumsuz etkiler. Çoğu durumda, performansı azaleden performans kabul edilebilir. Daha da önemlisi, JıT derleyicisi tarafından oluşturulan kod, derlemeyi tetikleyen işleme bağlanır. Birden çok işlem arasında paylaştırılamaz. Oluşturulan kodun bir uygulamanın birden çok üzerinde veya bir derleme kümesini paylaşan birden çok işlem arasında paylaşılmasına izin vermek için, ortak dil çalışma zamanı bir güncel derleme modunu destekler. Bu güncel derleme modu, MSIL derlemelerini JıT derleyicisi tarafından çok benzer şekilde yerel koda dönüştürmek için [Ngen. exe (yerel görüntü Oluşturucu)](../../docs/framework/tools/ngen-exe-native-image-generator.md) kullanır. Ancak, Ngen. exe işleminin işlemi, JıT derleyicisinden üç şekilde farklıdır:  
  
- Uygulama çalışırken değil uygulamayı çalıştırmadan önce MSIL 'den yerel koda dönüştürme gerçekleştirir.  
  
- Aynı anda tek bir yöntem yerine, bir derlemenin tamamını bir kez derler.  
  
- Oluşturulan kodu, diskteki bir dosya olarak yerel görüntü önbelleğinde devam ettirir.  
  
### <a name="code-verification"></a>Kod doğrulama  
 Bir yönetici, kodun doğrulamayı atlamasına izin veren bir güvenlik ilkesi kurmadığı sürece MSIL kodu, yerel koda derlemenin bir parçası olarak bir doğrulama işlemi iletmelidir. Doğrulama, kodun güvenli olup olmadığını öğrenmek için MSIL ve meta verileri inceler, bu da yalnızca erişim yetkisi olan bellek konumlarına erişir. Tür güvenliği nesneleri birbirlerinden yalıtmaya yardımcı olur ve bunları yanlışlıkla veya kötü amaçlı bozulmalara karşı korumanıza yardımcı olur. Ayrıca, kod üzerinde Güvenlik kısıtlamalarının güvenilir bir şekilde zorlanacağını güvence altına alır.  
  
 Çalışma zamanı, aşağıdaki deyimlerin önem derecesi türü güvenli olan kod için doğru olmasına bağlıdır:  
  
- Bir türe başvuru, başvurulmakta olan türle kesinlikle uyumludur.  
  
- Bir nesne üzerinde yalnızca uygun şekilde tanımlanmış işlemler çağrılır.  
  
- Kimlikler, iddia ettikleri şeydir.  
  
 Doğrulama işlemi sırasında, kodun bellek konumlarına erişebileceğini onaylama ve yalnızca düzgün tanımlanmış türler aracılığıyla metotları çağırma girişimi sırasında MSIL kodu incelenir. Örneğin, kod, bir nesnenin alanlarına bellek konumlarının taşmasına izin veren bir biçimde erişilmesine izin vermez. Ayrıca, yanlış MSIL tür güvenlik kuralları ihlaline yol açabildiğinden, MSIL 'nin doğru oluşturulup oluşturulmayacağını anlamak için doğrulama kodu inceler. Doğrulama işlemi, iyi tanımlanmış bir tür güvenli kod kümesi geçirir ve yalnızca tür kullanımı güvenli olan kodu geçirir. Ancak, bazı tür kullanımı güvenli kod, doğrulama işleminin bazı sınırlamaları ve tasarıma göre bazı diller, tam olarak tür kullanımı uyumlu kod üretmedikleri için doğrulamayı geçemeyebilir. Güvenlik ilkesi için tür kullanımı uyumlu kod gerekliyse ancak kod doğrulamayı geçemezse, kod çalıştırıldığında bir özel durum oluşturulur.  
  
 [Başa dön](#introduction)  
  
<a name="running_code"></a>
## <a name="running-code"></a>Kod çalıştırma  
 Ortak dil çalışma zamanı, yönetilen yürütmenin yürütme sırasında kullanılabilecek bir yerde ve hizmet almasını sağlayan altyapıyı sağlar. Bir yöntem çalıştırılmadan önce, işlemciye özel koda derlenmesi gerekir. MSIL 'nin oluşturulduğu her yöntem, ilk kez çağrıldığında JıT olarak derlenir ve sonra çalıştırılır. Yöntemin bir sonraki çalıştırılışında, var olan JıT derlenmiş yerel kod çalıştırılır. JıT derleme ve sonra kodu çalıştırma işlemi, yürütme tamamlanana kadar yinelenir.  
  
 Yürütme sırasında yönetilen kod, atık toplama, güvenlik, yönetilmeyen kodla birlikte çalışabilirlik, çapraz dil hata ayıklama desteği ve gelişmiş dağıtım ve sürüm oluşturma desteği gibi hizmetleri alır.  
  
 Microsoft Windows Vista 'da, işletim sistemi yükleyicisi, COFF üstbilgisindeki bir bit inceleyerek yönetilen modülleri denetler. Ayarlanan bit, yönetilen bir modül gösterir. Yükleyici yönetilen modülleri algılarsa, mscoree. dll dosyasını yükler ve `_CorValidateImage` ve yönetilen modül görüntüleri yüklenip kaldırıldığında yükleyiciyi bilgilendirir `_CorImageUnloading`. `_CorValidateImage` aşağıdaki eylemleri gerçekleştirir:  
  
1. Kodun geçerli yönetilen kod olmasını sağlar.  
  
2. Görüntüdeki giriş noktasını çalışma zamanındaki bir giriş noktasına dönüştürür.  
  
 64 bit Windows üzerinde `_CorValidateImage`, bellekteki görüntüyü PE32 ' den PE32 + biçimine dönüştürerek değiştirir.  
  
 [Başa dön](#introduction)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel bakış](../../docs/framework/get-started/overview.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../docs/standard/language-independence-and-language-independent-components.md)
- [Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../docs/standard/metadata-and-self-describing-components.md)
- [Ilasm.exe (IL Derleyici)](../../docs/framework/tools/ilasm-exe-il-assembler.md)
- [Güvenlik](../../docs/standard/security/index.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../docs/framework/interop/index.md)
- [Dağıtım](../../docs/framework/deployment/net-framework-applications.md)
- [.NET’te bütünleştirilmiş kodlar](assembly/index.md)
- [Uygulama Etki Alanları](../../docs/framework/app-domains/application-domains.md)
