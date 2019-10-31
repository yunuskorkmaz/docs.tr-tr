---
title: Hata Ayıklama Arabirimleri
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 07b39666637628102e9ffafd2c059ba0d4b51b92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097191"
---
# <a name="debugging-interfaces"></a>Hata Ayıklama Arabirimleri
Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Iclrdataenummemoryregion arabirimi](iclrdataenummemoryregions-interface.md)\
 Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.  
  
 [ICLRDataEnumMemoryRegionsCallback arabirimi](iclrdataenummemoryregionscallback-interface.md)\
 `EnumMemoryRegions` hata ayıklayıcıya rapor etmek için bir geri çağırma yöntemi sağlar, belirtilen bellek bölgesini numaralandırma denemesinin sonucudur.  
  
 [ICLRDataTarget arabirimi](iclrdatatarget-interface.md)\
 Hedef CLR işlemiyle etkileşim için yöntemler sağlar.  
  
 [ICLRDataTarget2 arabirimi](iclrdatatarget2-interface.md)\
 Hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim Hizmetleri katmanı tarafından kullanılan bir `ICLRDataTarget` alt sınıfı.  
  
 [ICLRDataTarget3 arabirimi](iclrdatatarget3-interface.md)\
 Özel durum bilgilerine erişim sağlayan [ICLRDataTarget2](iclrdatatarget2-interface.md) öğesinin bir alt sınıfı.  
  
 [ICLRDebugging arabirimi](iclrdebugging-interface.md)\
 Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.  
  
 [ICLRDebuggingLibraryProvider arabirimi](iclrdebugginglibraryprovider-interface.md)\
 Ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarının isteğe bağlı olarak bulunmasını ve yüklenmesine izin veren bir kitaplık sağlayıcısı geri çağırma arabirimi alan [ProvideLibrary Yöntemi](iclrdebugginglibraryprovider-providelibrary-method.md) yöntemini içerir.  
  
 [ICLRMetadataLocator arabirimi](iclrmetadatalocator-interface.md)\
 Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.  
  
 [ICorDebug arabirimi](icordebug-interface.md)\
 Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.  
  
 [ICorDebugAppDomain arabirimi](icordebugappdomain-interface.md)\
 Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.  
  
 [ICorDebugAppDomain2 arabirimi](icordebugappdomain2-interface.md)\
 Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar. Bu arabirim `ICorDebugAppDomain` arabiriminin bir uzantısıdır.  
  
 [ICorDebugAppDomain3 arabirimi](icordebugappdomain3-interface.md)\
 Uygulama etki alanında Windows Çalışma Zamanı türleriyle çalışmak için yöntemler sağlar. Bu arabirim, `ICorDebugAppDomain` ve `ICorDebugAppDomain2` arabirimlerinin bir uzantısıdır.  
  
 [ICorDebugAppDomain4 arabirimi](icordebugappdomain4-interface.md)\
 Bir COM çağrılabilir sarmalayıcısından yönetilen bir nesne almak için [ICorDebugAppDomain](icordebugappdomain-interface.md) arabirimini mantıksal olarak genişletir.  
  
 [ICorDebugAppDomainEnum arabirimi](icordebugappdomainenum-interface.md)\
 Numaralandırmadaki bir sonraki konumdan başlayarak belirtilen sayıda `ICorDebugAppDomain` değeri döndüren bir yöntem sağlar.  
  
 [Icorıbu Garrayvalue arabirimi](icordebugarrayvalue-interface.md)\
 Tek boyutlu veya çok boyutlu bir diziyi temsil eden `ICorDebugHeapValue` bir alt sınıfı.  
  
 [ICorDebugAssembly arabirimi](icordebugassembly-interface.md)\
 Bir derlemeyi temsil eder.  
  
 [ICorDebugAssembly2 arabirimi](icordebugassembly2-interface.md)\
 Bir derlemeyi temsil eder. Bu arabirim `ICorDebugAssembly` arabiriminin bir uzantısıdır.  
  
 [ICorDebugAssembly3 arabirimi](icordebugassembly3-interface.md)\
 Kapsayıcı derlemeler ve içerdikleri derlemeler için destek sağlamak üzere [ICorDebugAssembly](icordebugassembly-interface.md) arabirimini mantıksal olarak genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugAssemblyEnum arabirimi](icordebugassemblyenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugAssembly` dizilerini numaralandırır.  
  
 [ICorDebugBlockingObjectEnum arabirimi](icordebugblockingobjectenum-interface.md)\
 [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesi için bir Numaralandırıcı sağlar.  
  
 [ICorDebugBoxValue arabirimi](icordebugboxvalue-interface.md)\
 Paketlenmiş değer sınıf nesnesini temsil eden `ICorDebugHeapValue` alt sınıfı.  
  
 [ICorDebugBreakpoint arabirimi](icordebugbreakpoint-interface.md)\
 Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.  
  
 [ICorDebugBreakpointEnum arabirimi](icordebugbreakpointenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugBreakpoint` dizilerini numaralandırır.  
  
 [Icordebugzinciri arabirimi](icordebugchain-interface.md)\
 Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.  
  
 [ICorDebugChainEnum arabirimi](icordebugchainenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugChain` dizilerini numaralandırır.  
  
 [ICorDebugClass arabirimi](icordebugclass-interface.md)\
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür geneldir ise, `ICorDebugClass` örneklenmiş genel türü temsil eder.  
  
 [ICorDebugClass2 arabirimi](icordebugclass2-interface.md)\
 Bir genel sınıfı veya <xref:System.Type>türünde bir yöntem parametresi olan bir sınıfı temsil eder. Bu arabirim `ICorDebugClass`genişletir.  
  
 [ICorDebugCode arabirimi](icordebugcode-interface1.md)\
 Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
 [ICorDebugCode2 arabirimi](icordebugcode2-interface.md)\
 `ICorDebugCode`yeteneklerini genişleten yöntemler sağlar.  
  
 [ICorDebugCode3 arabirimi](icordebugcode3-interface.md)\
 Yönetilen bir dönüş değeri hakkında bilgi sağlamak için [ICorDebugCode](icordebugcode-interface1.md) ve [ICorDebugCode2](icordebugcode2-interface.md) genişleten bir yöntem sağlar.  
  
 [ICorDebugCode4 arabirimi](icordebugcode4-interface.md)\
 Bir işlevdeki yerel değişkenleri ve bağımsız değişkenleri numaralandırmak için hata ayıklayıcı sağlayan bir yöntem sağlar.  
  
 [ICorDebugCodeEnum arabirimi](icordebugcodeenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugCode` dizilerini numaralandırır.  
  
 [ICorDebugComObjectValue arabirimi](icordebugcomobjectvalue-interface.md)\
 Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.  
  
 [ICorDebugContext arabirimi](icordebugcontext-interface.md)\
 Bir bağlam nesnesini temsil eder. Bu arabirim henüz uygulanmamış.  
  
 [ICorDebugController arabirimi](icordebugcontroller-interface.md)\
 Kod yürütme bağlamının denetlenebileceği bir <xref:System.Diagnostics.Process> ya da <xref:System.AppDomain>bir kapsamı temsil eder.  
  
 [ICorDebugDataTarget arabirimi](icordebugdatatarget-interface.md)\
 Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.  
  
 [ICorDebugDataTarget2 arabirimi](icordebugdatatarget2-interface.md)\
 [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mantıksal olarak genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugDataTarget3 arabirimi](icordebugdatatarget3-interface.md)\
 Yüklü modüller hakkında bilgi sağlamak için [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mantıksal olarak genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [Icordebugdebugger gevent arabirimi](icordebugdebugevent-interface.md)\
 Tüm `ICorDebug` hata ayıklama olaylarının türeten temel arabirimi tanımlar. **Yalnızca .NET Native kullanılabilir.**  
  
 [Icorerrorgeditanddevam ErrorInfo arabirimi](icordebugeditandcontinueerrorinfo-interface.md)\
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [ICorDebugEditAndContinueSnapshot arabirimi](icordebugeditandcontinuesnapshot-interface.md)\
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [Icorı, Genum arabirimi](icordebugenum-interface1.md)\
 Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.  
  
 [Icordebugger Gerrorınfoenum arabirimi](icordebugerrorinfoenum-interface.md)\
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [Icorınpagegeval arabirimi](icordebugeval-interface.md)\
 Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.  
  
 [ICorDebugEval2 arabirimi](icordebugeval2-interface.md)\
 Genel türler için destek sağlamak üzere `ICorDebugEval` genişletir.  
  
 [Icordebugexceptiondebugger gevent arabirimi](icordebugexceptiondebugevent-interface.md)\
 Özel durum olaylarını desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugExceptionObjectCallStackEnum arabirimi](icordebugexceptionobjectcallstackenum-interface.md)\
 Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.  
  
 [ICorDebugExceptionObjectValue arabirimi](icordebugexceptionobjectvalue-interface.md)\
 Yönetilen bir özel durum nesnesinden yığın izleme bilgisi sağlamak için [ICorDebugObjectValue](icordebugobjectvalue-interface.md) arabirimini genişletir.  
  
 [ICorDebugFrame arabirimi](icordebugframe-interface.md)\
 Geçerli yığındaki bir çerçeveyi temsil eder.  
  
 [ICorDebugFrameEnum arabirimi](icordebugframeenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugFrame` dizilerini numaralandırır.  
  
 [ICorDebugFunction arabirimi](icordebugfunction-interface1.md)\
 Yönetilen bir işlevi veya yöntemi temsil eder.  
  
 [ICorDebugFunction2 arabirimi](icordebugfunction2-interface.md)\
 Yalnızca kendi kodum adım adım hata ayıklama için destek sağlamak üzere `ICorDebugFunction` mantıksal olarak genişletir.  
  
 [ICorDebugFunction3 arabirimi](icordebugfunction3-interface.md)\
 Bir ReJIT isteğinden koda erişim sağlamak için [ICorDebugFunction](icordebugfunction-interface1.md) arabirimini mantıksal olarak genişletir.  
  
 [ICorDebugFunctionBreakpoint arabirimi](icordebugfunctionbreakpoint-interface.md)\
 İşlevler içindeki kesme noktalarını desteklemek için `ICorDebugBreakpoint` genişletir.  
  
 [Icorıtcggcreferenceenum arabirimi](icordebuggcreferenceenum-interface.md)\
 Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.  
  
 [ICorDebugGenericValue arabirimi](icordebuggenericvalue-interface.md)\
 Tüm değerlere uygulanan `ICorDebugValue` alt sınıfı. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
 [ICorDebugGuidToTypeEnum arabirimi](icordebugguidtotypeenum-interface.md)\
 GUID 'Leri ve bunlara karşılık gelen `ICorDebugType` nesnelerini eşleyen bir nesne için bir Numaralandırıcı sağlar.  
  
 [Icorıınfo Ghandtavalue arabirimi](icordebughandlevalue-interface.md)\
 Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden bir `ICorDebugReferenceValue` alt sınıfı.  
  
 [ICorDebugHeapEnum arabirimi](icordebugheapenum-interface.md)\
 Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.  
  
 [ICorDebugHeapSegmentEnum arabirimi](icordebugheapsegmentenum-interface.md)\
 Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.  
  
 [ICorDebugHeapValue arabirimi](icordebugheapvalue-interface.md)\
 CLR çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eden `ICorDebugValue` alt sınıfı.  
  
 [ICorDebugHeapValue2 arabirimi](icordebugheapvalue2-interface1.md)\
 Çalışma zamanı tutamaçları için destek sağlayan `ICorDebugHeapValue` uzantısı.  
  
 [ICorDebugHeapValue3 arabirimi](icordebugheapvalue3-interface.md)\
 Nesnelerin monitör kilit özelliklerini gösterir.  
  
 [Icordebugilcode arabirimi](icordebugilcode-interface.md)\
 Ara dil (IL) kodu segmentini temsil eder.  
  
 [ICorDebugILCode2 arabirimi](icordebugilcode2-interface.md)\
 Bir işlevin yerel değişken imzasının belirtecini döndüren ve bir profiler 'ın belgelenmiş ara dili (IL) orijinal Yöntem Il uzaklıklarına eşleyen Yöntemler sağlamak için [ICorDebugILCode](icordebugilcode-interface.md) arabirimini mantıksal olarak genişletir.  
  
 [ICorDebugILFrame arabirimi](icordebugilframe-interface.md)\
 MSIL kodunun bir yığın çerçevesini temsil eder.  
  
 [ICorDebugILFrame2 arabirimi](icordebugilframe2-interface.md)\
 `ICorDebugILFrame`mantıksal uzantısı.  
  
 [ICorDebugILFrame3 arabirimi](icordebugilframe3-interface.md)\
 İşlevin dönüş değerini içeren bir yöntem sağlar.  
  
 [ICorDebugILFrame4 arabirimi](icordebugilframe4-interface.md)\
 Ara dil (IL) kodunun yığın çerçevesindeki yerel değişkenlere ve koda erişmenize imkan tanıyan yöntemler sağlar. Bir parametre, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere ve koda erişip erişemeyeceğini belirtir.  
  
 [Icordebugınstancefieldsymbol arabirimi](icordebuginstancefieldsymbol-interface.md)\
 Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugInternalFrame arabirimi](icordebuginternalframe-interface.md)\
 Hata ayıklayıcı için çerçeve türlerini tanımlar.  
  
 [ICorDebugInternalFrame2 arabirimi](icordebuginternalframe2-interface.md)\
 Yığın adresi ve [ICorDebugFrame](icordebugframe-interface.md) nesneleriyle ilişkili konum dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.  
  
 [ICorDebugLoadedModule arabirimi](icordebugloadedmodule-interface.md)\
 Yüklü bir modül hakkında bilgi sağlar. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugManagedCallback arabirimi](icordebugmanagedcallback-interface.md)\
 Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.  
  
 [ICorDebugManagedCallback2 arabirimi](icordebugmanagedcallback2-interface.md)\
 Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar. `ICorDebugManagedCallback2`, `ICorDebugManagedCallback`bir mantıksal uzantısıdır.  
  
 [ICorDebugManagedCallback3 arabirimi](icordebugmanagedcallback3-interface.md)\
 Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.  
  
 [ICorDebugMDA arabirimi](icordebugmda-interface.md)\
 Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.  
  
 [ICorDebugMemoryBuffer arabirimi](icordebugmemorybuffer-interface.md)\
 Bellek içi arabelleği temsil eder. **Yalnızca .NET Native kullanılabilir.**  
  
 [Icordebugmergedassemblyrecord arabirimi](icordebugmergedassemblyrecord-interface.md)\
 Birleştirilmiş bir derleme hakkında bilgi sağlar. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugMetaDataLocator arabirimi](icordebugmetadatalocator-interface.md)\
 Hata ayıklayıcıya meta veri bilgileri sağlar.  
  
 [ICorDebugModule arabirimi](icordebugmodule-interface.md)\
 Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.  
  
 [ICorDebugModule2 arabirimi](icordebugmodule2-interface.md)\
 `ICorDebugModule`için bir mantıksal uzantı işlevi görür.  
  
 [ICorDebugModule3 arabirimi](icordebugmodule3-interface.md)\
 Dinamik modül için simge okuyucu oluşturur.  
  
 [ICorDebugModuleBreakpoint arabirimi](icordebugmodulebreakpoint-interface.md)\
 Belirli modüllere erişim sağlamak için `ICorDebugBreakpoint` genişletir.  
  
 [Icordebugmoduledebugger gevent arabirimi](icordebugmoduledebugevent-interface.md)\
 Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugModuleEnum arabirimi](icordebugmoduleenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugModule` dizilerini numaralandırır.  
  
 [Icordebugmutabledatatarget arabirimi](icordebugmutabledatatarget-interface.md)\
 [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini, değişebilir veri hedeflerini destekleyecek şekilde genişletir.  
  
 [ICorDebugNativeFrame arabirimi](icordebugnativeframe-interface.md)\
 Yerel çerçeveler için kullanılan `ICorDebugFrame` özelleştirilmiş bir uygulama.  
  
 [ICorDebugNativeFrame2 arabirimi](icordebugnativeframe2-interface.md)\
 Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.  
  
 [ICorDebugObjectEnum arabirimi](icordebugobjectenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve nesnelerin dizilerini göreli sanal adreslere göre numaralandırır (RVA).  
  
 [ICorDebugObjectValue arabirimi](icordebugobjectvalue-interface.md)\
 Bir nesnesi içeren bir değeri temsil eden `ICorDebugValue` alt sınıfı.  
  
 [ICorDebugObjectValue2 arabirimi](icordebugobjectvalue2-interface.md)\
 Devralma ve geçersiz kılmaları desteklemek için `ICorDebugObjectValue` genişletir.  
  
 [ICorDebugProcess arabirimi](icordebugprocess-interface.md)\
 Yönetilen bir kodu yürüten bir işlemi temsil eder.  
  
 [ICorDebugProcess2 arabirimi](icordebugprocess2-interface1.md)\
 `ICorDebugProcess`mantıksal uzantısı.  
  
 [ICorDebugProcess3 arabirimi](icordebugprocess3-interface.md)\
 Özel hata ayıklayıcı bildirimlerini denetler.

 [ICorDebugProcess4 arabirimi](icordebugprocess4-interface.md)\
 İşlem dışı yürütme denetimi için destek sağlar.
  
 [ICorDebugProcess5 arabirimi](icordebugprocess5-interface.md)\
 Yönetilen yığına erişimi desteklemek, yönetilen nesnelerin çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcının uygulamanın yerel yerel görüntü önbelleğinden görüntü yükleyip yükleyemeyeceğini anlamak için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini genişletir.  
  
 [ICorDebugProcess6 arabirimi](icordebugprocess6-interface.md)\
 Yerel özel durum ayıklama olayları ve sanal modül bölünmesi içinde kodlanmış yönetilen hata ayıklama olaylarının kodunu çözme gibi özellikleri etkinleştirmek için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini mantıksal olarak genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugProcess7 arabirimi](icordebugprocess7-interface.md)\
 Hata ayıklayıcıyı, hedef işlemdeki bellek içi meta veri güncelleştirmelerini işleyecek şekilde yapılandıran bir yöntem sağlar.  
  
 [ICorDebugProcess8 arabirimi](icordebugprocess8-interface.md)\
 Belirli [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) özel durum geri çağırmaları türlerini etkinleştirmek veya devre dışı bırakmak Için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini mantıksal olarak genişletir.  
  
 [ICorDebugProcessEnum arabirimi](icordebugprocessenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugProcess` dizilerini numaralandırır.  
  
 [ICorDebugReferenceValue arabirimi](icordebugreferencevalue-interface.md)\
 Başvuru türlerini destekleyen `ICorDebugValue` alt sınıfı.  
  
 [ICorDebugRegisterSet arabirimi](icordebugregisterset-interface.md)\
 Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.  
  
 [ICorDebugRegisterSet2 arabirimi](icordebugregisterset2-interface.md)\
 64 ' den fazla kaydı olan donanım platformları için `ICorDebugRegisterSet` yeteneklerini genişletir.  
  
 [ICorDebugRemote arabirimi](icordebugremote-interface.md)\
 Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.  
  
 [ICorDebugRemoteTarget arabirimi](icordebugremotetarget-interface.md)\
 CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.  
  
 [Icorıınfo Gruntimeunwindadbleframe arabirimi](icordebugruntimeunwindableframe-interface.md)\
 Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.  
  
 [Icordebugstackyürüme arabirimi](icordebugstackwalk-interface.md)\
 İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.  
  
 [ICorDebugStaticFieldSymbol arabirimi](icordebugstaticfieldsymbol-interface.md)\
 Statik bir alan için hata ayıklama simgesi bilgisini temsil eder. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugStepper arabirimi](icordebugstepper-interface.md)\
 Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.  
  
 [ICorDebugStepper2 arabirimi](icordebugstepper2-interface1.md)\
 Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.  
  
 [ICorDebugStepperEnum arabirimi](icordebugstepperenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugStepper` dizilerini numaralandırır.  
  
 [ICorDebugStringValue arabirimi](icordebugstringvalue-interface.md)\
 Dize değerlerine uygulanan `ICorDebugHeapValue` alt sınıfı.  
  
 [ICorDebugSymbolProvider arabirimi](icordebugsymbolprovider-interface.md)\
 Hata ayıklama sembolü bilgilerini almak için kullanılabilecek yöntemler sağlar. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugSymbolProvider2 arabirimi](icordebugsymbolprovider2-interface.md)\
 Ek hata ayıklama sembol bilgilerini almak için [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) arabirimini mantıksal olarak genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugThread arabirimi](icordebugthread-interface.md)\
 Bir işlemdeki bir iş parçacığını temsil eder. Bir `ICorDebugThread` örneğinin kullanım ömrü, temsil ettiği iş parçacığının yaşam süresi ile aynıdır.  
  
 [ICorDebugThread2 arabirimi](icordebugthread2-interface.md)\
 `ICorDebugThread`için bir mantıksal uzantı işlevi görür.  
  
 [ICorDebugThread3 arabirimi](icordebugthread3-interface.md)\
 [Icordebugstackyürüme](icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.  
  
 [ICorDebugThread4 arabirimi](icordebugthread4-interface.md)\
 İş parçacığı engelleme bilgileri sağlar.  
  
 [ICorDebugThreadEnum arabirimi](icordebugthreadenum-interface1.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugThread` dizilerini numaralandırır.  
  
 [ICorDebugType arabirimi](icordebugtype-interface.md)\
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür geneldir ise, `ICorDebugType` örneklenmiş genel türü temsil eder.  
  
 [ICorDebugType2 arabirimi](icordebugtype2-interface.md)\
 Bir temel türün tür tanımlayıcısını veya karmaşık (Kullanıcı tanımlı) türünü almak için [ICorDebugType](icordebugtype-interface.md) arabirimini genişletir.  
  
 [ICorDebugTypeEnum arabirimi](icordebugtypeenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugType` dizilerini numaralandırır.  
  
 [ICorDebugUnmanagedCallback arabirimi](icordebugunmanagedcallback-interface.md)\
 CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.  
  
 [ICorDebugValue](icordebugvalue-interface.md)\
 Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.  
  
 [Icordebugvalue2](icordebugvalue2-interface.md)\
 `ICorDebugType`için destek sağlamak üzere `ICorDebugValue` genişletir.  
  
 [ICorDebugValue3 arabirimi](icordebugvalue3-interface.md)\
 2 GB 'den büyük diziler için destek sağlamak üzere "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 Belirli değerlere erişim sağlamak için `ICorDebugBreakpoint` genişletir.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 `ICorDebugEnum` yöntemleri uygular ve `ICorDebugValue` dizilerini numaralandırır.  
  
 [Icordebugvariablehome arabirimi](icordebugvariablehome-interface.md)\
 Bir işlevin yerel bir değişkenini veya bağımsız değişkenini temsil eder.  
  
 [Icordebugvariablehomeenum arabirimi](icordebugvariablehomeenum-interface.md)\
 Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı sağlar.  
  
 [ICorDebugVariableSymbol arabirimi](icordebugvariablesymbol-interface.md)\
 Bir değişken için hata ayıklama sembol bilgisini alır. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugVirtualUnwinder arabirimi](icordebugvirtualunwinder-interface.md)\
 Yığın geri sarma konusunda yardımcı olmak için yöntemler sağlar. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorPublish arabirimi](icorpublish-interface.md)\
 Yayınlama işlevinin genel arabirimi olarak işlev görür.  
  
 [ICorPublishAppDomain arabirimi](icorpublishappdomain-interface.md)\
 Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.  
  
 [ICorPublishAppDomainEnum arabirimi](icorpublishappdomainenum-interface.md)\
 , Bir işlem içinde mevcut olan `ICorPublishAppDomain` nesneleri koleksiyonunu gezme yöntemleri sağlar.  
  
 [ICorPublishEnum arabirimi](icorpublishenum-interface.md)\
 Numaralandırıcılar yayımlamak için soyut temel görevi görür.  
  
 [ICorPublishProcess arabirimi](icorpublishprocess-interface.md)\
 İşlemle ilgili bilgilere erişen yöntemler sağlar.  
  
 [ICorPublishProcessEnum arabirimi](icorpublishprocessenum-interface.md)\
 `ICorPublishProcess` nesnelerinin bir koleksiyonunu çapraz geçiş yapan yöntemler sağlar.  

 [Iosdacınterface arabirimi](isosdacinterface-interface.md)\
 `SOS`verilere erişmek için yardımcı yöntemler sağlar.

 [IXCLRDataMethodDefinition arabirimi](ixclrdatamethoddefinition-interface.md)\
 Yöntem tanımı hakkında bilgi sorgulamak için yöntemler sağlar.
 
 [IXCLRDataMethodInstance arabirimi](ixclrdatamethodinstance-interface.md)\
 Bir yöntem örneği hakkındaki bilgileri sorgulamak için yöntemler sağlar.
 
 [IXCLRDataModule arabirimi](ixclrdatamodule-interface.md)\
 Yüklü bir modülle ilgili bilgileri sorgulamak için yöntemler sağlar.
 
 [IXCLRDataProcess arabirimi](ixclrdataprocess-interface.md)\
 İşlem hakkındaki bilgileri sorgulamak için yöntemler sağlar.
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Ortak sınıflarda hata ayıklama](debugging-coclasses.md)\
 [Genel statik Işlevlerde hata ayıklama](debugging-global-static-functions.md)\
 [Numaralandırmalar hata ayıklaması](debugging-enumerations.md)\
 [Yapılarda hata ayıklama](debugging-structures.md)\
