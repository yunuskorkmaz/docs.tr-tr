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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160228"
---
# <a name="managed-execution-process"></a>Yönetilen Yürütme İşlemi
<a name="introduction"></a>Yönetilen yürütme işlemi, daha sonra bu konuda ayrıntılı olarak tartışılan aşağıdaki adımları içerir:  
  
1. [Derleyici seçimi.](#choosing_a_compiler)  
  
     Ortak dil çalışma zamanı tarafından sağlanan avantajları elde etmek için, çalışma süresini hedefleyen bir veya daha fazla dil derleyicisi kullanmanız gerekir.  
  
2. [Kodunuzu MSIL'e derleme](#compiling_to_msil).  
  
     Derleme, kaynak kodunuzu Microsoft ara diline (MSIL) çevirir ve gerekli meta verileri oluşturur.  
  
3. [MSIL'i yerel koda derleme.](#compiling_msil_to_native_code)  
  
     Yürütme zamanında, tam zamanında (JIT) derleyicisi MSIL'i yerel koda çevirir. Bu derleme sırasında, kodun tür güvenli olarak belirlenip belirlenemeyeceğini öğrenmek için kodun MSIL ve meta verileri inceleyen bir doğrulama işleminden geçmesi gerekir.  
  
4. [Çalışan kod](#running_code).  
  
     Ortak dil çalışma süresi, yürütmenin gerçekleşmesini sağlayan altyapıyı ve yürütme sırasında kullanılabilecek hizmetleri sağlar.  
  
<a name="choosing_a_compiler"></a>
## <a name="choosing-a-compiler"></a>Derleyici Seçme  
 Ortak dil çalışma zamanı (CLR) tarafından sağlanan avantajları elde etmek için Visual Basic, C#, Visual C++, F#veya Eyfel, Perl veya COBOL derleyicisi gibi çalışma süresini hedefleyen bir veya daha fazla dil derleyicisi kullanmanız gerekir.  
  
 Çok dilli bir yürütme ortamı olduğundan, çalışma zamanı çok çeşitli veri türlerini ve dil özelliklerini destekler. Kullandığınız dil derleyicisi hangi çalışma zamanı özelliklerinin kullanılabileni belirler ve kodunuzu bu özellikleri kullanarak tasarlarsınız. Derleyiciniz, çalışma saatini değil, kodunuzu kullanması gereken sözdizimini belirler. Bileşeninizin diğer dillerde yazılmış bileşenler tarafından tamamen kullanılabilir olması gerekiyorsa, bileşeninizin dışa aktarılan türleri yalnızca [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler'de](../../docs/standard/language-independence-and-language-independent-components.md) (CLS) yer alan dil özelliklerini ortaya çıkarmalıdır. Kodunuzun <xref:System.CLSCompliantAttribute> CLS uyumlu olduğundan emin olmak için özniteliği kullanabilirsiniz. Daha fazla bilgi için [bkz.](../../docs/standard/language-independence-and-language-independent-components.md)  
  
 [Başa dön](#introduction)  
  
<a name="compiling_to_msil"></a>
## <a name="compiling-to-msil"></a>MSIL'e Derleme  
 Yönetilen koda derleme yaparken, derleyici kaynak kodunuzu, yerel koda verimli bir şekilde dönüştürülebilen CPU'dan bağımsız bir yönerge ler kümesi olan Microsoft ara diline (MSIL) çevirir. MSIL, nesnelerüzerinde yükleme, depolama, başlatma ve arama yöntemlerinin yanı sıra aritmetik ve mantıksal işlemler, denetim akışı, doğrudan bellek erişimi, özel durum işleme ve diğer işlemler için yönergeler içerir. Kod çalıştırılmadan önce, MSIL cpu'ya özgü koda dönüştürülmelidir, genellikle [tam zamanında (JIT) derleyici](#compiling_msil_to_native_code)tarafından. Ortak dil çalışma süresi, desteklediği her bilgisayar mimarisi için bir veya daha fazla JIT derleyicisi sağladığından, aynı MSIL kümesi JIT tarafından derlenebilir ve desteklenen mimaride çalıştırılabilir.  
  
 Bir derleyici MSIL ürettiğinde, meta veri de üretir. Meta veriler, her türün tanımı, her türün üyelerinin imzaları, kodunuzu başvuran üyeler ve yürütme sırasında çalışma zamanının kullandığı diğer veriler de dahil olmak üzere kodunuzdaki türleri açıklar. MSIL ve meta veriler, çalıştırılabilir içerik için geçmişte kullanılan microsoft pe ve ortak nesne dosya biçimini (COFF) temel alan ve genişleten taşınabilir bir yürütülebilir (PE) dosyasında bulunur. MSIL veya yerel kodun yanı sıra meta verileri de barındıran bu dosya biçimi, işletim sisteminin ortak dil çalışma zamanı görüntülerini tanımasını sağlar. MSIL ile birlikte dosyada meta verilerin varlığı, kodunuzun kendisini tanımlamasını sağlar, bu da tür kitaplıklarına veya Arabirim Tanımı Dili'ne (IDL) gerek olmadığı anlamına gelir. Çalışma zamanı, yürütme sırasında gerektiğinde dosyadaki meta verileri bulur ve ayıklar.  
  
 [Başa dön](#introduction)  
  
<a name="compiling_msil_to_native_code"></a>
## <a name="compiling-msil-to-native-code"></a>MSIL'i Yerel Koda Derleme  
 Microsoft ara dilini (MSIL) çalıştırabilmek için önce, hedef makine mimarisi için ortak dil çalışma süresine göre yerel koda göre derlenmiş olması gerekir. .NET Framework bu dönüşümü gerçekleştirmek için iki yol sağlar:  
  
- Bir .NET Framework tam zamanında (JIT) derleyicisi.  
  
- .NET Framework [Ngen.exe (Yerli Görüntü Jeneratörü)](../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="compilation-by-the-jit-compiler"></a>JIT Derleyicisi tarafından derleme  
 JIT derlemesi, bir derlemenin içeriği yüklenip yürütüldüğünde, uygulama çalışma zamanında isteğe bağlı olarak MSIL'i yerel koda dönüştürür. Ortak dil çalışma süresi desteklenen her CPU mimarisi için bir JIT derleyicisi sağladığından, geliştiriciler JIT tarafından derlenebilecek ve farklı makine mimarilerine sahip farklı bilgisayarlarda çalıştırılabilen bir MSIL derlemekümesi oluşturabilir. Ancak, yönetilen kodunuz platforma özgü yerel API'leri veya platforma özgü sınıf kitaplığını çağrıyorsa, yalnızca bu işletim sisteminde çalışır.  
  
 JIT derlemesi, yürütme sırasında bazı kodların asla çağrılmama olasılığını dikkate alır. Pe dosyasındaki tüm MSIL'i yerel koda dönüştürmek için zaman ve bellek kullanmak yerine, yürütme sırasında gerektiğinde MSIL'i dönüştürür ve bu işlem bağlamında sonraki çağrılar için erişilebilir olacak şekilde ortaya çıkan yerel kodu bellekte depolar. Yükleyici, tür yüklendiğinde ve başharfe geçtiğinde bir türdeki her yönteme bir saplama oluşturur ve bağlar. Bir yöntem ilk kez çağrıldığında, saplama denetimi JIT derleyicisine geçirir, bu yöntem için MSIL'i yerel koda dönüştürür ve saplamayı doğrudan oluşturulan yerel koda işaret etmek üzere değiştirir. Bu nedenle, JIT tarafından derlenen yönteme sonraki çağrılar doğrudan yerel koda gider.  
  
### <a name="install-time-code-generation-using-ngenexe"></a>NGen.exe kullanarak Yükleme-Zaman Kodu Oluşturma  
 JIT derleyicisi, bu derlemede tanımlanan tek tek yöntemler çağrıldığında bir derlemenin MSIL'ini yerel koda dönüştürdüğü için, çalışma zamanında performansı olumsuz etkiler. Çoğu durumda, bu azalan performans kabul edilebilir. Daha da önemlisi, JIT derleyicisi tarafından oluşturulan kod derlemeyi tetikleyen işleme bağlıdır. Birden çok işlem arasında paylaşılamaz. Oluşturulan kodun bir uygulamanın birden çok daveti arasında veya bir derleme kümesini paylaşan birden çok işlem arasında paylaşılmasına izin vermek için, ortak dil çalışma süresi önceden bir derleme modunu destekler. Bu ileri-of-time derleme modu Çok JIT derleyici yaptığı gibi yerel kod msil derlemeleri dönüştürmek için [Ngen.exe (Yerli Görüntü Üreteci)](../../docs/framework/tools/ngen-exe-native-image-generator.md) kullanır. Ancak, Ngen.exe'nin çalışması JIT derleyicisinden üç şekilde farklıdır:  
  
- Uygulama çalışırken değil, uygulamayı çalıştırmadan önce MSIL'den yerel koda dönüştürme gerçekleştirir.  
  
- Bir seferde bir yöntem yerine, bir seferde tüm derlemeyi derler.  
  
- Yerel Resim Önbelleğinde oluşturulan kodu diskte bir dosya olarak devam eder.  
  
### <a name="code-verification"></a>Kod Doğrulama  
 Yerel koda derlemesinin bir parçası olarak, bir yönetici kodun doğrulamayı atlamasına izin veren bir güvenlik ilkesi oluşturmadığı sürece, MSIL kodu bir doğrulama işlemini geçirmelidir. Doğrulama, kodun tür güvenli olup olmadığını öğrenmek için MSIL ve meta verileri inceler, bu da yalnızca erişmeye yetkili olduğu bellek konumlarına eriştiği anlamına gelir. Tür güvenliği nesneleri birbirinden yalıtmalarına ve yanlışlıkla veya kötü amaçlı bozulmadan korumaya yardımcı olur. Ayrıca, kod üzerindeki güvenlik kısıtlamalarının güvenilir bir şekilde uygulanabileceğine dair güvence de sağlar.  
  
 Çalışma süresi, doğrulanabilir şekilde güvenli kod için aşağıdaki ifadelerin doğru olduğu gerçeğine dayanır:  
  
- Bir türe yapılan başvuru, başvurulan türle kesinlikle uyumludur.  
  
- Yalnızca uygun tanımlanmış işlemler bir nesneye çağrılır.  
  
- Kimlikler iddia ettikleri gibi.  
  
 Doğrulama işlemi sırasında, MSIL kodu, kodun bellek konumlarına ve arama yöntemlerine yalnızca doğru tanımlanmış türler aracılığıyla erişebileceğini doğrulamak amacıyla incelenir. Örneğin, kod bir nesnenin alanlarına bellek konumlarının aşılmasına izin verecek şekilde erişilmesine izin veremez. Ayrıca doğrulama, MSIL'in doğru oluşturulup oluşturulmadığını belirlemek için kodu denetler, çünkü yanlış MSIL tür güvenliği kurallarının ihlaline neden olabilir. Doğrulama işlemi, iyi tanımlanmış bir tür güvenli kod kümesinden geçer ve yalnızca güvenli tür kodundan geçer. Ancak, bazı tür güvenli kod doğrulama işleminin bazı sınırlamaları nedeniyle doğrulamayı geçemeyebilir ve bazı diller, tasarım gereği doğrulanabilir şekilde tür de güvenli kod üretmez. Güvenlik ilkesi tarafından tür güvenli kod gerekliyse, ancak kod doğrulamadan geçmiyorsa, kod çalıştırıldığında bir özel durum atılır.  
  
 [Başa dön](#introduction)  
  
<a name="running_code"></a>
## <a name="running-code"></a>Çalışan Kod  
 Ortak dil çalışma süresi, yönetilen yürütmenin gerçekleşmesini sağlayan altyapıyı ve yürütme sırasında kullanılabilecek hizmetleri sağlar. Bir yöntem çalıştırılabilmek için önce işlemciye özgü kodiçin derlenmiş olması gerekir. MSIL'in oluşturulduğu her yöntem, ilk çağrıldığında JIT tarafından derlenir ve çalıştırılır. Yöntem bir sonraki çalıştırılda, varolan JIT derlenmiş yerel kod çalıştırılır. JIT derleme ve ardından kodu çalıştırma işlemi yürütme tamamlanana kadar yinelenir.  
  
 Yürütme sırasında yönetilen kod, çöp toplama, güvenlik, yönetilmeyen kodla birlikte çalışabilirlik, diller arası hata ayıklama desteği ve gelişmiş dağıtım ve sürüm desteği gibi hizmetleri alır.  
  
 Microsoft Windows Vista'da, işletim sistemi yükleyicisi COFF üstbilgisinde biraz inceleyerek yönetilen modülleri denetler. Ayarlanan bit, yönetilen bir modülü gösterir. Yükleyici yönetilen modülleri algılarsa, mscoree.dll `_CorValidateImage` yükler `_CorImageUnloading` ve yönetilen modül görüntüleri yüklenip boşaltıldığında yükleyiciye bildirir. `_CorValidateImage`aşağıdaki eylemleri gerçekleştirir:  
  
1. Kodun geçerli yönetilen kod olmasını sağlar.  
  
2. Görüntüdeki giriş noktasını çalışma zamanında bir giriş noktasına değiştirir.  
  
 64 bit Windows'da, `_CorValidateImage` BELLEKteki görüntüyü PE32'den PE32+ formatına dönüştürerek değiştirir.  
  
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
