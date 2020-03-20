---
title: Hata Ayıklama Arabirimleri
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: c4b9cdc2bc90096ab7c3b041bd8aa2742b48c35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179159"
---
# <a name="debugging-interfaces"></a>Hata Ayıklama Arabirimleri
Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ICLRDataEnumMemoryRegions Arayüzü](iclrdataenummemoryregions-interface.md)\
 Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.  
  
 [ICLRDataEnumMemoryRegionsCallback Arabirimi](iclrdataenummemoryregionscallback-interface.md)\
 Hata ayıklama, `EnumMemoryRegions` bellek belirli bir bölge metodlamak için bir girişimin sonucu bildirmek için bir geri arama yöntemi sağlar.  
  
 [ICLRDataTarget Arayüzü](iclrdatatarget-interface.md)\
 Hedef CLR işlemiyle etkileşim için yöntemler sağlar.  
  
 [ICLRDataTarget2 Arayüzü](iclrdatatarget2-interface.md)\
 Bunun bir `ICLRDataTarget` alt sınıfı, hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim hizmetleri katmanı tarafından kullanılır.  
  
 [ICLRDataTarget3 Arayüzü](iclrdatatarget3-interface.md)\
 Özel durum bilgilerine erişim sağlayan [ICLRDataTarget2](iclrdatatarget2-interface.md) alt sınıfı.  
  
 [ICLRDebugging Arabirimi](iclrdebugging-interface.md)\
 Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.  
  
 [ICLRDebuggingLibrarySağlayıcı Arabirimi](iclrdebugginglibraryprovider-interface.md)\
 Ortak dil çalışma zamanı sürümüne özgü hata ayıklama kitaplıkları bulunan ve isteğe bağlı olarak yüklenen sağlayan bir kitaplık sağlayıcısı geri arama arabirimi alır [ProvideLibrary Yöntemi](iclrdebugginglibraryprovider-providelibrary-method.md) yöntemini içerir.  
  
 [ICLRMetadataLocator Arabirimi](iclrmetadatalocator-interface.md)\
 Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.  
  
 [ICorDebug Arayüzü](icordebug-interface.md)\
 Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.  
  
 [ICorDebugAppDomain Arayüzü](icordebugappdomain-interface.md)\
 Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.  
  
 [ICorDebugAppDomain2 Arayüzü](icordebugappdomain2-interface.md)\
 Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar. Bu arabirim `ICorDebugAppDomain` arabirimin bir uzantısıdır.  
  
 [ICorDebugAppDomain3 Arayüzü](icordebugappdomain3-interface.md)\
 Bir uygulama etki alanında Windows Runtime türleri ile çalışmak için yöntemler sağlar. Bu arabirim `ICorDebugAppDomain` ve `ICorDebugAppDomain2` arabirimlerin bir uzantısıdır.  
  
 [ICorDebugAppDomain4 Arayüzü](icordebugappdomain4-interface.md)\
 Com çağrılabilir sarıcıdan yönetilen bir nesne almak için Mantıksal olarak [ICorDebugAppDomain](icordebugappdomain-interface.md) arabirimini genişletir.  
  
 [ICorDebugAppDomainEnum Arayüzü](icordebugappdomainenum-interface.md)\
 Numaralandırmada bir sonraki konumdan başlayarak belirli sayıda `ICorDebugAppDomain` değer döndüren bir yöntem sağlar.  
  
 [ICorDebugArrayValue Arayüzü](icordebugarrayvalue-interface.md)\
 Bunun bir `ICorDebugHeapValue` alt sınıfı tek boyutlu veya çok boyutlu bir diziyi temsil eder.  
  
 [ICorDebugAssembly Arayüzü](icordebugassembly-interface.md)\
 Bir derlemeyi temsil eder.  
  
 [ICorDebugAssembly2 Arayüzü](icordebugassembly2-interface.md)\
 Bir derlemeyi temsil eder. Bu arabirim `ICorDebugAssembly` arabirimin bir uzantısıdır.  
  
 [ICorDebugAssembly3 Arayüz](icordebugassembly3-interface.md)\
 Mantıksal olarak, kapsayıcı derlemeleri ve bunların içerdiği derlemeler için destek sağlamak için [ICorDebugAssembly](icordebugassembly-interface.md) arabirimini genişletir. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugAssemblyEnum Arayüzü](icordebugassemblyenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugAssembly` oyalar.  
  
 [ICorDebugBlockingObjectEnum Arabirimi](icordebugblockingobjectenum-interface.md)\
 [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesi için bir sayısallaştırıcı sağlar.  
  
 [ICorDebugBoxValue Arayüzü](icordebugboxvalue-interface.md)\
 Bunun bir `ICorDebugHeapValue` alt sınıfı kutulanmış bir değer sınıfı nesnesini temsil eder.  
  
 [ICorDebugBreakpoint Arabirimi](icordebugbreakpoint-interface.md)\
 Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.  
  
 [ICorDebugBreakpointEnum Arabirimi](icordebugbreakpointenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugBreakpoint` oyalar.  
  
 [ICorDebugChain Arayüzü](icordebugchain-interface.md)\
 Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.  
  
 [ICorDebugChainEnum Arayüzü](icordebugchainenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugChain` oyalar.  
  
 [ICorDebugClass Arabirimi](icordebugclass-interface.md)\
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür genelse, `ICorDebugClass` anlık olmayan genel türü temsil eder.  
  
 [ICorDebugClass2 Arabirimi](icordebugclass2-interface.md)\
 Genel bir sınıfı veya yöntem parametresi <xref:System.Type>türüne sahip bir sınıfı temsil eder. Bu arayüz `ICorDebugClass`genişletir.  
  
 [ICorDebugCode Arayüzü](icordebugcode-interface1.md)\
 Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
 [ICorDebugCode2 Arayüzü](icordebugcode2-interface.md)\
 `ICorDebugCode`Yeteneklerini genişleten yöntemler sağlar.  
  
 [ICorDebugCode3 Arayüzü](icordebugcode3-interface.md)\
 Yönetilen bir iade değeri hakkında bilgi sağlamak için [ICorDebugCode](icordebugcode-interface1.md) ve [ICorDebugCode2'yi](icordebugcode2-interface.md) genişleten bir yöntem sağlar.  
  
 [ICorDebugCode4 Arayüzü](icordebugcode4-interface.md)\
 Bir hata ayıklayanın bir işlevdeki yerel değişkenleri ve bağımsız değişkenleri sayısalatmasını sağlayan bir yöntem sağlar.  
  
 [ICorDebugCodeEnum Arayüz](icordebugcodeenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugCode` oyalar.  
  
 [ICorDebugComObjectValue Arabirimi](icordebugcomobjectvalue-interface.md)\
 Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.  
  
 [ICorDebugContext Arayüzü](icordebugcontext-interface.md)\
 Bir bağlam nesnesini temsil eder. Bu arabirim henüz uygulanmamış.  
  
 [ICorDebugController Arayüzü](icordebugcontroller-interface.md)\
 Kod yürütme bağlamında <xref:System.AppDomain>denetlenebilen bir <xref:System.Diagnostics.Process> kapsamı temsil eder.  
  
 [ICorDebugDataTarget Arayüzü](icordebugdatatarget-interface.md)\
 Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.  
  
 [ICorDebugDataTarget2 Arayüzü](icordebugdatatarget2-interface.md)\
 Mantıksal olarak [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini genişletir. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugDataTarget3 Arayüzü](icordebugdatatarget3-interface.md)\
 Yüklenen modüller hakkında bilgi sağlamak için Mantıksal olarak [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini genişletir. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugDebugOlay Arabirimi](icordebugdebugevent-interface.md)\
 Tüm `ICorDebug` hata ayıklama olaylarının türetildiği temel arabirimi tanımlar. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugEditAndContinueErrorInfo Arayüzü](icordebugeditandcontinueerrorinfo-interface.md)\
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [ICorDebugEditAndContinueSnapshot Arayüzü](icordebugeditandcontinuesnapshot-interface.md)\
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [ICorDebugEnum Arayüzü](icordebugenum-interface1.md)\
 Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.  
  
 [ICorDebugErrorInfoEnum Arayüz](icordebugerrorinfoenum-interface.md)\
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [ICorDebugEval Arayüzü](icordebugeval-interface.md)\
 Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.  
  
 [ICorDebugEval2 Arayüzü](icordebugeval2-interface.md)\
 Genel `ICorDebugEval` türler için destek sağlamak için genişletir.  
  
 [ICorDebugExceptionDebugOlay Arabirimi](icordebugexceptiondebugevent-interface.md)\
 Özel durum olaylarını desteklemek için [ICorDebugDebugEvent](icordebugdebugevent-interface.md) arabirimini genişletir. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugExceptionObjectCallStackEnum Arayüzü](icordebugexceptionobjectcallstackenum-interface.md)\
 Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.  
  
 [ICorDebugExceptionObjectValue Arabirimi](icordebugexceptionobjectvalue-interface.md)\
 Yönetilen bir özel durum nesnesinden yığın izleme bilgileri sağlamak için [ICorDebugObjectValue](icordebugobjectvalue-interface.md) arabirimini genişletir.  
  
 [ICorDebugFrame Arabirimi](icordebugframe-interface.md)\
 Geçerli yığındaki bir çerçeveyi temsil eder.  
  
 [ICorDebugFrameEnum Arayüzü](icordebugframeenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugFrame` oyalar.  
  
 [ICorDebugFunction Arayüzü](icordebugfunction-interface1.md)\
 Yönetilen bir işlevi veya yöntemi temsil eder.  
  
 [ICorDebugFunction2 Arayüzü](icordebugfunction2-interface.md)\
 Mantıksal olarak `ICorDebugFunction` Sadece Kodum adım hata ayıklama için destek sağlamak için uzanır.  
  
 [ICorDebugFunction3 Arayüzü](icordebugfunction3-interface.md)\
 Mantıksal olarak, Bir ReJIT isteğinden koda erişim sağlamak için [ICorDebugFunction](icordebugfunction-interface1.md) arabirimini genişletir.  
  
 [ICorDebugFunctionBreakpoint Arabirimi](icordebugfunctionbreakpoint-interface.md)\
 Işlevler `ICorDebugBreakpoint` içindeki kesme noktalarını desteklemek için genişletir.  
  
 [ICorDebugGCReferenceEnum Arayüzü](icordebuggcreferenceenum-interface.md)\
 Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.  
  
 [ICorDebugGenericValue Arayüzü](icordebuggenericvalue-interface.md)\
 Bunun bir `ICorDebugValue` alt sınıfı tüm değerler için geçerlidir. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
 [ICorDebugGuidToTypeEnum Arayüzü](icordebugguidtotypeenum-interface.md)\
 GUID'leri ve bunların karşılık gelen `ICorDebugType` nesnelerini eşleyen bir nesne için bir sayısallaştırıcı sağlar.  
  
 [ICorDebugHandleValue Arabirimi](icordebughandlevalue-interface.md)\
 Bunun bir `ICorDebugReferenceValue` alt sınıfı, hata ayıklamanın çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eder.  
  
 [ICorDebugHeapEnum Arayüzü](icordebugheapenum-interface.md)\
 Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.  
  
 [ICorDebugHeapSegmentEnum Arayüzü](icordebugheapsegmentenum-interface.md)\
 Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.  
  
 [ICorDebugHeapValue Arabirimi](icordebugheapvalue-interface.md)\
 Bunun bir `ICorDebugValue` alt sınıfı CLR çöp toplayıcısı tarafından toplanan bir nesneyi temsil eder.  
  
 [ICorDebugHeapValue2 Arabirimi](icordebugheapvalue2-interface1.md)\
 Bunun bir `ICorDebugHeapValue` uzantısı çalışma zamanı tutamaçları için destek sağlar.  
  
 [ICorDebugHeapValue3 Arabirimi](icordebugheapvalue3-interface.md)\
 Nesnelerin monitör kilit özelliklerini gösterir.  
  
 [ICorDebugILCode Arayüzü](icordebugilcode-interface.md)\
 Ara dil (IL) kodunun bir kesimini temsil eder.  
  
 [ICorDebugILCode2 Arayüzü](icordebugilcode2-interface.md)\
 Mantıksal olarak, bir işlevin yerel değişken imzasının belirteci döndürülen yöntemleri sağlamak ve bir profil oluşturucunun enstrümantif ara dili (IL) uzaklıklarını özgün yöntem IL uzaklıklarına göre eşleyen yöntemler sağlamak için [ICorDebugILCode](icordebugilcode-interface.md) arabirimini mantıksal olarak genişletir.  
  
 [ICorDebugILFrame Arabirimi](icordebugilframe-interface.md)\
 MSIL kodunun bir yığın çerçevesini temsil eder.  
  
 [ICorDebugILFrame2 Arabirim](icordebugilframe2-interface.md)\
 Mantıksal bir `ICorDebugILFrame`uzantısı .  
  
 [ICorDebugILFrame3 Arabirim](icordebugilframe3-interface.md)\
 İşlevin dönüş değerini içeren bir yöntem sağlar.  
  
 [ICorDebugILFrame4 Arabirim](icordebugilframe4-interface.md)\
 Ara dil (IL) kodu yığını çerçevesinde yerel değişkenlere ve koda erişmenizi sağlayan yöntemler sağlar. Parametre, hata ayıklayıcının profil oluşturucu ReJIT enstrümantasyonuna eklenen değişkenlere ve koda erişimi olup olmadığını belirtir.  
  
 [ICorDebugInstanceFieldSymbol Arabirimi](icordebuginstancefieldsymbol-interface.md)\
 Örnek alan için hata ayıklama simgesi bilgilerini temsil eder. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugInternalFrame Arabirimi](icordebuginternalframe-interface.md)\
 Hata ayıklayıcı için çerçeve türlerini tanımlar.  
  
 [ICorDebugInternalFrame2 Arabirimi](icordebuginternalframe2-interface.md)\
 [ICorDebugFrame](icordebugframe-interface.md) nesneleri ile ilgili yığın adresi ve konumu da dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.  
  
 [ICorDebugLoadedModule Arayüzü](icordebugloadedmodule-interface.md)\
 Yüklenen modül hakkında bilgi sağlar. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugManagedCallback Arayüzü](icordebugmanagedcallback-interface.md)\
 Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.  
  
 [ICorDebugManagedCallback2 Arayüzü](icordebugmanagedcallback2-interface.md)\
 Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar. `ICorDebugManagedCallback2`'nin `ICorDebugManagedCallback`mantıksal bir uzantısıdır.  
  
 [ICorDebugManagedCallback3 Arayüzü](icordebugmanagedcallback3-interface.md)\
 Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.  
  
 [ICorDebugMDA Arayüzü](icordebugmda-interface.md)\
 Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.  
  
 [ICorDebugMemoryBuffer Arabirimi](icordebugmemorybuffer-interface.md)\
 Bellek içi arabelleği temsil eder. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugMergedAssemblyRecord Arabirimi](icordebugmergedassemblyrecord-interface.md)\
 Birleştirilmiş derleme hakkında bilgi sağlar. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugMeta DataLocator Arayüzü](icordebugmetadatalocator-interface.md)\
 Hata ayıklayıcıya meta veri bilgileri sağlar.  
  
 [ICorDebugModule Arayüzü](icordebugmodule-interface.md)\
 Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.  
  
 [ICorDebugModule2 Arayüzü](icordebugmodule2-interface.md)\
 `ICorDebugModule`Mantıksal bir uzantısı olarak hizmet vermektedir.  
  
 [ICorDebugModule3 Arayüz](icordebugmodule3-interface.md)\
 Dinamik modül için simge okuyucu oluşturur.  
  
 [ICorDebugModuleBreakpoint Arabirimi](icordebugmodulebreakpoint-interface.md)\
 Belirli `ICorDebugBreakpoint` modüllere erişim sağlamak için genişletir.  
  
 [ICorDebugModuleDebugOlay Arabirimi](icordebugmoduledebugevent-interface.md)\
 Modül düzeyindeki olayları desteklemek için [ICorDebugDebugEvent](icordebugdebugevent-interface.md) arabirimini genişletir. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugModuleEnum Arayüz](icordebugmoduleenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugModule` oyalar.  
  
 [ICorDebugMutableDataTarget Arayüzü](icordebugmutabledatatarget-interface.md)\
 [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mutable veri hedeflerini desteklemek için genişletir.  
  
 [ICorDebugNativeFrame Arayüzü](icordebugnativeframe-interface.md)\
 Yerel çerçeveler `ICorDebugFrame` için kullanılan özel bir uygulama.  
  
 [ICorDebugNativeFrame2 Arayüzü](icordebugnativeframe2-interface.md)\
 Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.  
  
 [ICorDebugObjectEnum Arayüzü](icordebugobjectenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve nesne dizilerini göreli sanal adreslerine (RVAs) göre sıralar.  
  
 [ICorDebugObjectValue Arabirimi](icordebugobjectvalue-interface.md)\
 Bunun bir `ICorDebugValue` alt sınıfı, bir nesne içeren bir değeri temsil eder.  
  
 [ICorDebugObjectValue2 Arabirimi](icordebugobjectvalue2-interface.md)\
 `ICorDebugObjectValue` Devralmayı desteklemek için genişletir ve geçersiz kılar.  
  
 [ICorDebugProcess Arayüzü](icordebugprocess-interface.md)\
 Yönetilen bir kodu yürüten bir işlemi temsil eder.  
  
 [ICorDebugProcess2 Arayüzü](icordebugprocess2-interface1.md)\
 Mantıksal bir `ICorDebugProcess`uzantısı .  
  
 [ICorDebugProcess3 Arayüzü](icordebugprocess3-interface.md)\
 Özel hata ayıklayıcı bildirimlerini denetler.

 [ICorDebugProcess4 Arayüz](icordebugprocess4-interface.md)\
 İşlem yürütme denetimi dışında destek sağlar.
  
 [ICorDebugProcess5 Arayüzü](icordebugprocess5-interface.md)\
 Yönetilen yığına erişimi desteklemek, yönetilen nesnelerin çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcının uygulamanın yerel görüntü önbelleğinden görüntü yükleyip yüklemediğini belirlemek için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini genişletir.  
  
 [ICorDebugProcess6 Arayüzü](icordebugprocess6-interface.md)\
 Yerel özel durum hata ayıklama olaylarında kodlanmış yönetilen hata ayıklama olaylarını çözme ve sanal modül bölme gibi özellikleri etkinleştirmek için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini mantıksal olarak genişletir. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugProcess7 Arayüzü](icordebugprocess7-interface.md)\
 Hata ayıklama işlemini hedef işlemdeki bellek içi meta veri güncelleştirmelerini işletmek üzere yapılandıran bir yöntem sağlar.  
  
 [ICorDebugProcess8 Arayüzü](icordebugprocess8-interface.md)\
 Mantıksal olarak [ICorDebugProcess](icordebugprocess-interface.md) arabirimini belirli [iCorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) özel durum geri aramalarını etkinleştirmek veya devre dışı kılabilir.  
  
 [ICorDebugProcessEnum Arayüzü](icordebugprocessenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugProcess` oyalar.  
  
 [ICorDebugReferenceValue Arayüzü](icordebugreferencevalue-interface.md)\
 Bu alt `ICorDebugValue` sınıf başvuru türlerini destekler.  
  
 [ICorDebugRegisterSet Arayüzü](icordebugregisterset-interface.md)\
 Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.  
  
 [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)\
 64'ten fazla `ICorDebugRegisterSet` kaydı olan donanım platformlarının yeteneklerini genişletir.  
  
 [ICorDebugUzaktan Arayüzü](icordebugremote-interface.md)\
 Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.  
  
 [ICorDebugRemoteTarget Arayüzü](icordebugremotetarget-interface.md)\
 CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.  
  
 [ICorDebugRuntimeUnwindableFrame Arayüzü](icordebugruntimeunwindableframe-interface.md)\
 Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.  
  
 [ICorDebugStackWalk Arayüzü](icordebugstackwalk-interface.md)\
 İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.  
  
 [ICorDebugStaticFieldSymbol Arayüzü](icordebugstaticfieldsymbol-interface.md)\
 Statik bir alan için hata ayıklama simgesi bilgilerini temsil eder. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugStepper Arayüzü](icordebugstepper-interface.md)\
 Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.  
  
 [ICorDebugStepper2 Arayüzü](icordebugstepper2-interface1.md)\
 Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.  
  
 [ICorDebugStepperEnum Arayüzü](icordebugstepperenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugStepper` oyalar.  
  
 [ICorDebugStringValue Arabirimi](icordebugstringvalue-interface.md)\
 Bunun bir `ICorDebugHeapValue` alt sınıfı dize değerleri için geçerlidir.  
  
 [ICorDebugSymbolProvider Arayüzü](icordebugsymbolprovider-interface.md)\
 Hata ayıklama simgesi bilgilerini almak için kullanılabilecek yöntemler sağlar. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugSymbolProvider2 Arayüzü](icordebugsymbolprovider2-interface.md)\
 Mantıksal olarak ek hata ayıklama sembolü bilgilerini almak için [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) arabirimini genişletir. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugThread Arayüzü](icordebugthread-interface.md)\
 Bir işlemdeki bir iş parçacığını temsil eder. Bir `ICorDebugThread` örneğin ömrü, temsil ettiği iş parçacığının ömrüyle aynıdır.  
  
 [ICorDebugThread2 Arayüzü](icordebugthread2-interface.md)\
 `ICorDebugThread`Mantıksal bir uzantısı olarak hizmet vermektedir.  
  
 [ICorDebugThread3 Arayüzü](icordebugthread3-interface.md)\
 [ICorDebugStackWalk](icordebugstackwalk-interface.md) ve ilgili arayüzler için giriş noktası sağlar.  
  
 [ICorDebugThread4 Arayüzü](icordebugthread4-interface.md)\
 İş parçacığı engelleme bilgileri sağlar.  
  
 [ICorDebugThreadEnum Arayüzü](icordebugthreadenum-interface1.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugThread` oyalar.  
  
 [ICorDebugType Arayüzü](icordebugtype-interface.md)\
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür genelse, `ICorDebugType` anlık genel türünü temsil eder.  
  
 [ICorDebugType2 Arayüzü](icordebugtype2-interface.md)\
 Bir taban türünün veya karmaşık (kullanıcı tanımlı) türünün tür tanımlayıcısını almak için [ICorDebugType](icordebugtype-interface.md) arabirimini genişletir.  
  
 [ICorDebugTypeEnum Arayüzü](icordebugtypeenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugType` oyalar.  
  
 [ICorDebugYönetilmeyenCallback Arabirimi](icordebugunmanagedcallback-interface.md)\
 CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.  
  
 [ıcordebugvalue](icordebugvalue-interface.md)\
 Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 Destek `ICorDebugValue` sağlamak için `ICorDebugType`genişletir.  
  
 [ICorDebugValue3 Arayüzü](icordebugvalue3-interface.md)\
 "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir ve 2 GB'dan büyük diziler için destek sağlar.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 Belirli `ICorDebugBreakpoint` değerlere erişim sağlamak için genişletir.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugValue` oyalar.  
  
 [ICorDebugVariableHome Arayüzü](icordebugvariablehome-interface.md)\
 Yerel bir değişkeni veya bir işlevin bağımsız değişkenini temsil eder.  
  
 [ICorDebugVariableHomeEnum Arayüzü](icordebugvariablehomeenum-interface.md)\
 Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir sayısallaştırıcı sağlar.  
  
 [ICorDebugVariableSymbol Arayüzü](icordebugvariablesymbol-interface.md)\
 Bir değişken için hata ayıklama sembolü bilgilerini alır. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorDebugVirtualUnwinder Arayüzü](icordebugvirtualunwinder-interface.md)\
 Yığın gevşemesine yardımcı olacak yöntemler sağlar. **Yalnızca .NET Native'de kullanılabilir.**  
  
 [ICorPublish Arayüzü](icorpublish-interface.md)\
 Yayınlama işlevinin genel arabirimi olarak işlev görür.  
  
 [iCorPublishAppDomain Arayüzü](icorpublishappdomain-interface.md)\
 Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.  
  
 [ICorPublishAppDomainEnum Arayüzü](icorpublishappdomainenum-interface.md)\
 Şu anda bir işlem `ICorPublishAppDomain` içinde bulunan nesnelerin bir koleksiyon çapraz yöntemleri sağlar.  
  
 [ICorPublishEnum Arayüzü](icorpublishenum-interface.md)\
 Numaralandırıcılar yayımlamak için soyut temel görevi görür.  
  
 [ICorPublishProcess Arayüzü](icorpublishprocess-interface.md)\
 İşlemle ilgili bilgilere erişen yöntemler sağlar.  
  
 [ICorPublishProcessEnum Arayüz](icorpublishprocessenum-interface.md)\
 `ICorPublishProcess` Nesneler koleksiyonunda geçiş yapan yöntemler sağlar.  

 [ISOSDacInterface Arayüzü](isosdacinterface-interface.md)\
 `SOS`Verilere erişmek için yardımcı yöntemler sağlar.

 [IXCLRDataMethodDefinition Arayüzü](ixclrdatamethoddefinition-interface.md)\
 Yöntem tanımı yla ilgili bilgileri sorgulama yöntemleri sağlar.

 [IXCLRDataMethodInstance Arabirimi](ixclrdatamethodinstance-interface.md)\
 Yöntem örneği hakkında bilgi sorgulama yöntemleri sağlar.

 [IXCLRDataModule Arabirimi](ixclrdatamodule-interface.md)\
 Yüklenen modül hakkında bilgi sorgulama yöntemleri sağlar.

 [IXCLRDataProcess Arabirimi](ixclrdataprocess-interface.md)\
 Bir işlem hakkında bilgi sorgulama yöntemleri sağlar.
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Coclasses](debugging-coclasses.md)\
 [Genel Statik Fonksiyonları Hata Ayıklama](debugging-global-static-functions.md)\
 [Hata Ayıklama Hesaplamaları](debugging-enumerations.md)\
 [Hata Ayıklama Yapıları](debugging-structures.md)\
