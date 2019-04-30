---
title: Hata Ayıklama Arabirimleri
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d939063aaefb00d4db3de604df0dbd1b2175bf95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698427"
---
# <a name="debugging-interfaces"></a>Hata Ayıklama Arabirimleri
Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Iclrdataenummemoryregions arabirimi](iclrdataenummemoryregions-interface.md)\
 Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.  
  
 [Iclrdataenummemoryregionscallback arabirimi](iclrdataenummemoryregionscallback-interface.md)\
 İçin bir geri arama yöntemi sağlar `EnumMemoryRegions` hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için.  
  
 [Iclrdatatarget arabirimi](iclrdatatarget-interface.md)\
 Hedef CLR işlemiyle etkileşim için yöntemler sağlar.  
  
 [Iclrdatatarget2 arabirimi](iclrdatatarget2-interface.md)\
 Öğesinin `ICLRDataTarget` , veri erişim Hizmetleri düzeyi tarafından hedef işlemde sanal bellek bölümlerini işlemek için kullanılır.  
  
 [Iclrdatatarget3 arabirimi](iclrdatatarget3-interface.md)\
 Öğesinin [Iclrdatatarget2](iclrdatatarget2-interface.md) , özel durum bilgilerine erişim sağlar.  
  
 [Iclrdebugging arabirimi](iclrdebugging-interface.md)\
 Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.  
  
 [Iclrdebugginglibraryprovider arabirimi](iclrdebugginglibraryprovider-interface.md)\
 İçerir [ProvideLibrary yöntemi](iclrdebugginglibraryprovider-providelibrary-method.md) kitaplık sağlayıcı ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarına ve yüklenecek isteğe bağlı olmasını sağlayan bir geri arama arabirimini alan yöntemi.  
  
 [Iclrmetadatalocator arabirimi](iclrmetadatalocator-interface.md)\
 Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.  
  
 [Icordebug arabirimi](icordebug-interface.md)\
 Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.  
  
 [Icordebugappdomain arabirimi](icordebugappdomain-interface.md)\
 Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.  
  
 [Icordebugappdomain2 arabirimi](icordebugappdomain2-interface.md)\
 Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar. Bu arabirim uzantısıdır `ICorDebugAppDomain` arabirimi.  
  
 [Icordebugappdomain3 arabirimi](icordebugappdomain3-interface.md)\
 Çalışmak için yöntemler sağlar [!INCLUDE[wrt](../../../../includes/wrt-md.md)] uygulama etki alanında türleri. Bu arabirim uzantısıdır `ICorDebugAppDomain` ve `ICorDebugAppDomain2` arabirimleri.  
  
 [Icordebugappdomain4 arabirimi](icordebugappdomain4-interface.md)\
 Mantıksal olarak genişletir [Icordebugappdomain](icordebugappdomain-interface.md) COM çağrılabilir sarmalayıcısı yönetilen bir nesneye almak için arabirim.  
  
 [Icordebugappdomainenum arabirimi](icordebugappdomainenum-interface.md)\
 Belirtilen sayıda döndüren bir yöntem sağlar `ICorDebugAppDomain` sonraki konumdan başlayarak değerleri.  
  
 [Icordebugarrayvalue arabirimi](icordebugarrayvalue-interface.md)\
 Öğesinin `ICorDebugHeapValue` temsil eden tek boyutlu veya çok boyutlu bir dizi.  
  
 [Icordebugassembly arabirimi](icordebugassembly-interface.md)\
 Bir derlemeyi temsil eder.  
  
 [Icordebugassembly2 arabirimi](icordebugassembly2-interface.md)\
 Bir derlemeyi temsil eder. Bu arabirim uzantısıdır `ICorDebugAssembly` arabirimi.  
  
 [Icordebugassembly3 arabirimi](icordebugassembly3-interface.md)\
 Mantıksal olarak genişletir [Icordebugassembly](icordebugassembly-interface.md) kapsayıcı derlemeleri ve bunların içerdiği derlemeleri için destek sağlamak için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugassemblyenum arabirimi](icordebugassemblyenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugAssembly` dizileri.  
  
 [Icordebugblockingobjectenum arabirimi](icordebugblockingobjectenum-interface.md)\
 Bir listesi için bir numaralandırıcı sağlar [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapıları.  
  
 [Icordebugboxvalue arabirimi](icordebugboxvalue-interface.md)\
 Öğesinin `ICorDebugHeapValue` paketlenmiş değer sınıf nesnesini temsil eden.  
  
 [Icordebugbreakpoint arabirimi](icordebugbreakpoint-interface.md)\
 Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.  
  
 [Icordebugbreakpointenum arabirimi](icordebugbreakpointenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugBreakpoint` dizileri.  
  
 [Icordebugchain arabirimi](icordebugchain-interface.md)\
 Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.  
  
 [Icordebugchainenum arabirimi](icordebugchainenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugChain` dizileri.  
  
 [Icordebugclass arabirimi](icordebugclass-interface.md)\
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür genelse, `ICorDebugClass` örneklenmemiş genel türü temsil eder.  
  
 [Icordebugclass2 arabirimi](icordebugclass2-interface.md)\
 Genel bir sınıf veya türündeki bir yöntem parametresi olan bir sınıfı temsil eden <xref:System.Type>. Bu arabirim genişletir `ICorDebugClass`.  
  
 [Icordebugcode arabirimi](icordebugcode-interface1.md)\
 Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
 [Icordebugcode2 arabirimi](icordebugcode2-interface.md)\
 Özelliklerini genişleten yöntemler sağlar `ICorDebugCode`.  
  
 [Icordebugcode3 arabirimi](icordebugcode3-interface.md)\
 Genişleten bir yöntem sağlar [Icordebugcode](icordebugcode-interface1.md) ve [Icordebugcode2](icordebugcode2-interface.md) yönetilen bir dönüş değeri hakkında bilgi sağlamak için.  
  
 [Icordebugcode4 arabirimi](icordebugcode4-interface.md)\
 Bir işlevdeki bağımsız değişkenler ve yerel değişkenler numaralandırmak bir hata ayıklayıcı sağlayan bir yöntem sağlar.  
  
 [Icordebugcodeenum arabirimi](icordebugcodeenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugCode` dizileri.  
  
 [Icordebugcomobjectvalue arabirimi](icordebugcomobjectvalue-interface.md)\
 Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.  
  
 [Icordebugcontext arabirimi](icordebugcontext-interface.md)\
 Bir bağlam nesnesini temsil eder. Bu arabirim henüz uygulanmamış.  
  
 [Icordebugcontroller arabirimi](icordebugcontroller-interface.md)\
 Bir kapsamı temsil eder bir <xref:System.Diagnostics.Process> veya <xref:System.AppDomain>, hangi kod yürütme bağlamının denetlenebileceği.  
  
 [Icordebugdatatarget arabirimi](icordebugdatatarget-interface.md)\
 Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.  
  
 [Icordebugdatatarget2 arabirimi](icordebugdatatarget2-interface.md)\
 Mantıksal olarak genişletir [Icordebugdatatarget](icordebugdatatarget-interface.md) arabirimi. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugdatatarget3 arabirimi](icordebugdatatarget3-interface.md)\
 Mantıksal olarak genişletir [Icordebugdatatarget](icordebugdatatarget-interface.md) yüklü modülleri hakkında bilgi sağlamak için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugdebugevent arabirimi](icordebugdebugevent-interface.md)\
 Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olaylarını türetilir. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugeditandcontinueerrorınfo arabirimi](icordebugeditandcontinueerrorinfo-interface.md)\
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [Icordebugeditandcontinuesnapshot arabirimi](icordebugeditandcontinuesnapshot-interface.md)\
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [Icordebugenum arabirimi](icordebugenum-interface1.md)\
 Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.  
  
 [Icordebugerrorınfoenum arabirimi](icordebugerrorinfoenum-interface.md)\
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [Icordebugeval arabirimi](icordebugeval-interface.md)\
 Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.  
  
 [Icordebugeval2 arabirimi](icordebugeval2-interface.md)\
 Genişletir `ICorDebugEval` genel türler için destek sağlamak için.  
  
 [Icordebugexceptiondebugevent arabirimi](icordebugexceptiondebugevent-interface.md)\
 Genişletir [Icordebugdebugevent](icordebugdebugevent-interface.md) özel durum olaylarının desteklemek için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugexceptionobjectcallstackenum arabirimi](icordebugexceptionobjectcallstackenum-interface.md)\
 Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.  
  
 [Icordebugexceptionobjectvalue arabirimi](icordebugexceptionobjectvalue-interface.md)\
 Genişletir [Icordebugobjectvalue](icordebugobjectvalue-interface.md) bir yönetilen özel durum nesnesinden yığın izleme bilgisi sağlamak için arabirim.  
  
 [Icordebugframe arabirimi](icordebugframe-interface.md)\
 Geçerli yığındaki bir çerçeveyi temsil eder.  
  
 [Icordebugframeenum arabirimi](icordebugframeenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugFrame` dizileri.  
  
 [ICorDebugFunction arabirimi](icordebugfunction-interface1.md)\
 Yönetilen bir işlevi veya yöntemi temsil eder.  
  
 [Icordebugfunction2 arabirimi](icordebugfunction2-interface.md)\
 Mantıksal olarak genişletir `ICorDebugFunction` yalnızca kendi kodum adım adım hata ayıklama için destek sağlamak için.  
  
 [Icordebugfunction3 arabirimi](icordebugfunction3-interface.md)\
 Mantıksal olarak genişletir [ICorDebugFunction](icordebugfunction-interface1.md) ReJIT istekten koda erişim sağlamak için arabirim.  
  
 [Icordebugfunctionbreakpoint arabirimi](icordebugfunctionbreakpoint-interface.md)\
 Genişletir `ICorDebugBreakpoint` işlevlerdeki kesme noktalarını desteklemek için.  
  
 [Icordebuggcreferenceenum arabirimi](icordebuggcreferenceenum-interface.md)\
 Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.  
  
 [Icordebuggenericvalue arabirimi](icordebuggenericvalue-interface.md)\
 Öğesinin `ICorDebugValue` tüm değerlere uygulanır. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
 [Icordebugguidtotypeenum arabirimi](icordebugguidtotypeenum-interface.md)\
 Bunlara karşılık gelen eşleyen nesne için bir numaralandırıcı sağlar `ICorDebugType` nesneleri.  
  
 [Icordebughandlevalue arabirimi](icordebughandlevalue-interface.md)\
 Öğesinin `ICorDebugReferenceValue` için hata ayıklayıcı çöp toplama işlemi için bir tanıtıcı oluşturduğu bir başvuru değeri temsil eder.  
  
 [Icordebugheapenum arabirimi](icordebugheapenum-interface.md)\
 Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.  
  
 [Icordebugheapsegmentenum arabirimi](icordebugheapsegmentenum-interface.md)\
 Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.  
  
 [Icordebugheapvalue arabirimi](icordebugheapvalue-interface.md)\
 Öğesinin `ICorDebugValue` CLR çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eder.  
  
 [Icordebugheapvalue2 arabirimi](icordebugheapvalue2-interface1.md)\
 ' In bir uzantısı `ICorDebugHeapValue` , çalışma zamanı işleçlerine ilişkin destek sağlar.  
  
 [Icordebugheapvalue3 arabirimi](icordebugheapvalue3-interface.md)\
 Nesnelerin monitör kilit özelliklerini gösterir.  
  
 [Icordebugılcode arabirimi](icordebugilcode-interface.md)\
 Ara dil (IL) kodu kesimini temsil eder.  
  
 [Icordebugılcode2 arabirimi](icordebugilcode2-interface.md)\
 Mantıksal olarak genişletir [Icordebugılcode](icordebugilcode-interface.md) yönelik bir işlevin yerel değişken imzası belirtecini döndürür ve bir profil oluşturucunun Araçlı Ara dil (IL) map yöntemleri sağlamak için arabirimi kaydırır IL özgün yöntemi kaydırır.  
  
 [Icordebugılframe arabirimi](icordebugilframe-interface.md)\
 MSIL kodunun bir yığın çerçevesini temsil eder.  
  
 [Icordebugılframe2 arabirimi](icordebugilframe2-interface.md)\
 Öğesinin mantıksal uzantısı `ICorDebugILFrame`.  
  
 [Icordebugılframe3 arabirimi](icordebugilframe3-interface.md)\
 İşlevin dönüş değerini içeren bir yöntem sağlar.  
  
 [Icordebugılframe4 arabirimi](icordebugilframe4-interface.md)\
 Yerel değişkenleri ve Ara dil (IL) kodu bir yığın çerçevesi kodu erişim olanak tanıyan yöntemler sağlar. Bir parametre, hata ayıklayıcı değişkenleri ve ReJIT izleme profil oluşturucu, eklenen kod erişimi olup olmadığını belirtir.  
  
 [Icordebugınstancefieldsymbol arabirimi](icordebuginstancefieldsymbol-interface.md)\
 Bir örnek alanıyla hata ayıklama sembolü bilgilerini temsil eder. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugınternalframe arabirimi](icordebuginternalframe-interface.md)\
 Hata ayıklayıcı için çerçeve türlerini tanımlar.  
  
 [Icordebugınternalframe2 arabirimi](icordebuginternalframe2-interface.md)\
 Yığın adresi ve ilişkili olarak dahil olmak üzere, iç çerçeveler hakkında bilgi sağlar [Icordebugframe](icordebugframe-interface.md) nesneleri.  
  
 [Icordebugloadedmodule arabirimi](icordebugloadedmodule-interface.md)\
 Yüklenen bir modülün hakkında bilgi sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugmanagedcallback arabirimi](icordebugmanagedcallback-interface.md)\
 Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.  
  
 [Icordebugmanagedcallback2 arabirimi](icordebugmanagedcallback2-interface.md)\
 Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar. `ICorDebugManagedCallback2` öğesinin mantıksal uzantısıdır `ICorDebugManagedCallback`.  
  
 [Icordebugmanagedcallback3 arabirimi](icordebugmanagedcallback3-interface.md)\
 Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.  
  
 [Icordebugmda arabirimi](icordebugmda-interface.md)\
 Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.  
  
 [Icordebugmemorybuffer arabirimi](icordebugmemorybuffer-interface.md)\
 Bir bellek arabelleğini temsil eder. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugmergedassemblyrecord arabirimi](icordebugmergedassemblyrecord-interface.md)\
 Birleştirilmiş bir derleme hakkında bilgi sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugmetadatalocator arabirimi](icordebugmetadatalocator-interface.md)\
 Hata ayıklayıcıya meta veri bilgileri sağlar.  
  
 [Icordebugmodule arabirimi](icordebugmodule-interface.md)\
 Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.  
  
 [Icordebugmodule2 arabirimi](icordebugmodule2-interface.md)\
 Bir mantıksal uzantısı olarak işlev görür `ICorDebugModule`.  
  
 [Icordebugmodule3 arabirimi](icordebugmodule3-interface.md)\
 Dinamik modül için simge okuyucu oluşturur.  
  
 [Icordebugmodulebreakpoint arabirimi](icordebugmodulebreakpoint-interface.md)\
 Genişletir `ICorDebugBreakpoint` belirli modüllere erişim sağlamak için.  
  
 [Icordebugmoduledebugevent arabirimi](icordebugmoduledebugevent-interface.md)\
 Genişletir [Icordebugdebugevent](icordebugdebugevent-interface.md) Modül düzeyinde olaylar desteklemek için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugmoduleenum arabirimi](icordebugmoduleenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugModule` dizileri.  
  
 [Icordebugmutabledatatarget arabirimi](icordebugmutabledatatarget-interface.md)\
 Genişletir [Icordebugdatatarget](icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.  
  
 [Icordebugnativeframe arabirimi](icordebugnativeframe-interface.md)\
 Öğesinin özelleşmiş uygulaması `ICorDebugFrame` yerel çerçeveler için kullanılır.  
  
 [Icordebugnativeframe2 arabirimi](icordebugnativeframe2-interface.md)\
 Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.  
  
 [Icordebugobjectenum arabirimi](icordebugobjectenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve bunların göreli sanal adreslerine (RVA) göre nesne dizilerini numaralandırır.  
  
 [Icordebugobjectvalue arabirimi](icordebugobjectvalue-interface.md)\
 Öğesinin `ICorDebugValue` temsil eden bir nesne içeren bir değer.  
  
 [Icordebugobjectvalue2 arabirimi](icordebugobjectvalue2-interface.md)\
 Genişletir `ICorDebugObjectValue` devralma ve geçersiz kılmaları desteklemek için.  
  
 [Icordebugprocess arabirimi](icordebugprocess-interface.md)\
 Yönetilen bir kodu yürüten bir işlemi temsil eder.  
  
 [Icordebugprocess2 arabirimi](icordebugprocess2-interface1.md)\
 Öğesinin mantıksal uzantısı `ICorDebugProcess`.  
  
 [Icordebugprocess3 arabirimi](icordebugprocess3-interface.md)\
 Özel hata ayıklayıcı bildirimlerini denetler.

 [ICorDebugProcess4 arabirimi](icordebugprocess4-interface.md)\
 İşlem yürütme denetimi dışında için destek sağlar.
  
 [Icordebugprocess5 arabirimi](icordebugprocess5-interface.md)\
 Genişletir [Icordebugprocess](icordebugprocess-interface.md) yerel, yönetilen nesnelerin Çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcı uygulamadan görüntüleri yükleyip yüklemediğini belirlemek için yönetilen yığına erişimi desteklemek için arabirimi Yerel görüntü önbelleği.  
  
 [Icordebugprocess6 arabirimi](icordebugprocess6-interface.md)\
 Mantıksal olarak genişletir [Icordebugprocess](icordebugprocess-interface.md) yerel özel durum hata ayıklama olaylarını ve sanal modül bölme kodlanmış yönetilen hata ayıklama olaylarını kod çözme gibi özellikleri etkinleştirmek için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugprocess7 arabirimi](icordebugprocess7-interface.md)\
 Hedef işlem, bellek içi meta veri güncelleştirmeleri işlemek için hata ayıklayıcı yapılandıran bir yöntem sağlar.  
  
 [Icordebugprocess8 arabirimi](icordebugprocess8-interface.md)\
 Mantıksal olarak genişletir [Icordebugprocess](icordebugprocess-interface.md) etkinleştirme veya devre dışı belirli türlerdeki arabirimi [Icordebugmanagedcallback2](icordebugmanagedcallback2-interface.md) özel durum geri aramalarını.  
  
 [Icordebugprocessenum arabirimi](icordebugprocessenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugProcess` dizileri.  
  
 [Icordebugreferencevalue arabirimi](icordebugreferencevalue-interface.md)\
 Öğesinin `ICorDebugValue` başvuru türlerini destekler.  
  
 [Icordebugregisterset arabirimi](icordebugregisterset-interface.md)\
 Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.  
  
 [Icordebugregisterset2 arabirimi](icordebugregisterset2-interface.md)\
 Yeteneklerini genişletir `ICorDebugRegisterSet` 64'den fazla kayda sahip donanım platformları için.  
  
 [Icordebugremote arabirimi](icordebugremote-interface.md)\
 Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.  
  
 [Icordebugremotetarget arabirimi](icordebugremotetarget-interface.md)\
 CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.  
  
 [Icordebugruntimeunwindableframe arabirimi](icordebugruntimeunwindableframe-interface.md)\
 Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.  
  
 [Icordebugstackwalk arabirimi](icordebugstackwalk-interface.md)\
 İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.  
  
 [Icordebugstaticfieldsymbol arabirimi](icordebugstaticfieldsymbol-interface.md)\
 Statik bir alan için hata ayıklama bilgilerini temsil eder. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugStepper arabirimi](icordebugstepper-interface.md)\
 Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.  
  
 [Icordebugstepper2 arabirimi](icordebugstepper2-interface1.md)\
 Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.  
  
 [Icordebugstepperenum arabirimi](icordebugstepperenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugStepper` dizileri.  
  
 [Icordebugstringvalue arabirimi](icordebugstringvalue-interface.md)\
 Öğesinin `ICorDebugHeapValue` dize değerleri için geçerlidir.  
  
 [Icordebugsymbolprovider arabirimi](icordebugsymbolprovider-interface.md)\
 Hata ayıklama bilgilerini almak için kullanılan yöntemler sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugsymbolprovider2 arabirimi](icordebugsymbolprovider2-interface.md)\
 Mantıksal olarak genişletir [Icordebugsymbolprovider](icordebugsymbolprovider-interface.md) ek hata ayıklama bilgilerini almak için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugthread arabirimi](icordebugthread-interface.md)\
 Bir işlemdeki bir iş parçacığını temsil eder. Yaşam süresi bir `ICorDebugThread` örneğidir ömrü, temsil ettiği iş parçacığı ile aynı.  
  
 [Icordebugthread2 arabirimi](icordebugthread2-interface.md)\
 Bir mantıksal uzantısı olarak işlev görür `ICorDebugThread`.  
  
 [Icordebugthread3 arabirimi](icordebugthread3-interface.md)\
 Giriş noktası sağlar [Icordebugstackwalk](icordebugstackwalk-interface.md) ve karşılık gelen arabirimleri.  
  
 [Icordebugthread4 arabirimi](icordebugthread4-interface.md)\
 İş parçacığı engelleme bilgileri sağlar.  
  
 [Icordebugthreadenum arabirimi](icordebugthreadenum-interface1.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugThread` dizileri.  
  
 [Icordebugtype arabirimi](icordebugtype-interface.md)\
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür genelse, `ICorDebugType` örneklenmiş genel türü temsil eder.  
  
 [Icordebugtype2 arabirimi](icordebugtype2-interface.md)\
 Genişletir [Icordebugtype](icordebugtype-interface.md) türü tanımlayıcısı bir temel türü veya karmaşık türü (kullanıcı tanımlı) almak için arabirim.  
  
 [Icordebugtypeenum arabirimi](icordebugtypeenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugType` dizileri.  
  
 [Icordebugunmanagedcallback arabirimi](icordebugunmanagedcallback-interface.md)\
 CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.  
  
 [Icordebugvalue](icordebugvalue-interface.md)\
 Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.  
  
 [Icordebugvalue2](icordebugvalue2-interface.md)\
 Genişletir `ICorDebugValue` için destek sağlamak üzere `ICorDebugType`.  
  
 [Icordebugvalue3 arabirimi](icordebugvalue3-interface.md)\
 2 GB'den daha büyük diziler için destek sağlamak için "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.  
  
 [Icordebugvaluebreakpoint](icordebugvaluebreakpoint-interface.md)\
 Genişletir `ICorDebugBreakpoint` belirli değerlere erişim sağlamak için.  
  
 [Icordebugvalueenum](icordebugvalueenum-interface.md)\
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugValue` dizileri.  
  
 [Icordebugvariablehome arabirimi](icordebugvariablehome-interface.md)\
 Bir yerel değişken veya işlev bağımsız değişkeni temsil eder.  
  
 [Icordebugvariablehomeenum arabirimi](icordebugvariablehomeenum-interface.md)\
 Bir işlevdeki bağımsız değişkenler ve yerel değişkenler için bir numaralandırıcı sağlar.  
  
 [Icordebugvariablesymbol arabirimi](icordebugvariablesymbol-interface.md)\
 Bir değişken için hata ayıklama bilgilerini alır. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugvirtualunwinder arabirimi](icordebugvirtualunwinder-interface.md)\
 Yığın geriye doğru izleme yardımcı olmak için yöntemleri sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icorpublish arabirimi](icorpublish-interface.md)\
 Yayınlama işlevinin genel arabirimi olarak işlev görür.  
  
 [Icorpublishappdomain arabirimi](icorpublishappdomain-interface.md)\
 Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.  
  
 [Icorpublishappdomainenum arabirimi](icorpublishappdomainenum-interface.md)\
 Koleksiyonunu geçirmek için yöntemler sağlar `ICorPublishAppDomain` şu anda bir işlem içinde varolan nesneleri.  
  
 [Icorpublishenum arabirimi](icorpublishenum-interface.md)\
 Numaralandırıcılar yayımlamak için soyut temel görevi görür.  
  
 [Icorpublishprocess arabirimi](icorpublishprocess-interface.md)\
 İşlemle ilgili bilgilere erişen yöntemler sağlar.  
  
 [Icorpublishprocessenum arabirimi](icorpublishprocessenum-interface.md)\
 Koleksiyonunu geçirmek için yöntemler sağlar `ICorPublishProcess` nesneleri.  

 [ISOSDacInterface arabirimi](isosdacinterface-interface.md)\
 Verilere erişmek için yardımcı yöntemleri sağlar `SOS`.

 [IXCLRDataMethodDefinition arabirimi](ixclrdatamethoddefinition-interface.md)\
 Bir yöntemin tanımı hakkında bilgi sorgulamak için yöntemler sağlar.
 
 [IXCLRDataMethodInstance arabirimi](ixclrdatamethodinstance-interface.md)\
 Metot örneği hakkında bilgi sorgulamak için yöntemler sağlar.
 
 [IXCLRDataModule arabirimi](ixclrdatamodule-interface.md)\
 Yüklenen bir modülün hakkında bilgi sorgulamak için yöntemler sağlar.
 
 [IXCLRDataProcess arabirimi](ixclrdataprocess-interface.md)\
 Bir işlem hakkında bilgi sorgulamak için yöntemler sağlar.
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata ayıklama coclass'ları](debugging-coclasses.md)\
 [Hata ayıklama genel statik işlevleri](debugging-global-static-functions.md)\
 [Hata ayıklama numaralandırmaları](debugging-enumerations.md)\
 [Hata ayıklama yapıları](debugging-structures.md)\
