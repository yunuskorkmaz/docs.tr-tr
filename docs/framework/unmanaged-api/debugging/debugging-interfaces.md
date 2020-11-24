---
title: Hata Ayıklama Arabirimleri
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: a3dd81ceaab2ba467d4c8ca091c1c2219040a273
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676302"
---
# <a name="debugging-interfaces"></a>Hata Ayıklama Arabirimleri

Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Iclrdataenummemoryregion arabirimi](iclrdataenummemoryregions-interface.md)\
 Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.  
  
 [ICLRDataEnumMemoryRegionsCallback arabirimi](iclrdataenummemoryregionscallback-interface.md)\
 `EnumMemoryRegions`Hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için bir geri arama yöntemi sağlar.  
  
 [ICLRDataTarget arabirimi](iclrdatatarget-interface.md)\
 Hedef CLR işlemiyle etkileşim için yöntemler sağlar.  
  
 [ICLRDataTarget2 arabirimi](iclrdatatarget2-interface.md)\
 `ICLRDataTarget`Hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim Hizmetleri katmanı tarafından kullanılan bir alt sınıfı.  
  
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
  
 [ICorDebugAppDomain Arabirimi](icordebugappdomain-interface.md)\
 Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.  
  
 [ICorDebugAppDomain2 arabirimi](icordebugappdomain2-interface.md)\
 Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar. Bu arabirim, arabiriminin bir uzantısıdır `ICorDebugAppDomain` .  
  
 [ICorDebugAppDomain3 arabirimi](icordebugappdomain3-interface.md)\
 Uygulama etki alanında Windows Çalışma Zamanı türleriyle çalışmak için yöntemler sağlar. Bu arabirim, ve arabirimlerinin bir uzantısıdır `ICorDebugAppDomain` `ICorDebugAppDomain2` .  
  
 [ICorDebugAppDomain4 arabirimi](icordebugappdomain4-interface.md)\
 Bir COM çağrılabilir sarmalayıcısından yönetilen bir nesne almak için [ICorDebugAppDomain](icordebugappdomain-interface.md) arabirimini mantıksal olarak genişletir.  
  
 [ICorDebugAppDomainEnum arabirimi](icordebugappdomainenum-interface.md)\
 Numaralandırmadaki bir sonraki konumdan başlayarak belirtilen sayıda değeri döndüren bir yöntem sağlar `ICorDebugAppDomain` .  
  
 [Icorıbu Garrayvalue arabirimi](icordebugarrayvalue-interface.md)\
 `ICorDebugHeapValue`Tek boyutlu veya çok boyutlu diziyi temsil eden öğesinin alt sınıfı.  
  
 [ICorDebugAssembly arabirimi](icordebugassembly-interface.md)\
 Bir derlemeyi temsil eder.  
  
 [ICorDebugAssembly2 arabirimi](icordebugassembly2-interface.md)\
 Bir derlemeyi temsil eder. Bu arabirim, arabiriminin bir uzantısıdır `ICorDebugAssembly` .  
  
 [ICorDebugAssembly3 arabirimi](icordebugassembly3-interface.md)\
 Kapsayıcı derlemeler ve içerdikleri derlemeler için destek sağlamak üzere [ICorDebugAssembly](icordebugassembly-interface.md) arabirimini mantıksal olarak genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugAssemblyEnum arabirimi](icordebugassemblyenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugAssembly` .  
  
 [ICorDebugBlockingObjectEnum arabirimi](icordebugblockingobjectenum-interface.md)\
 [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesi için bir Numaralandırıcı sağlar.  
  
 [ICorDebugBoxValue Arabirimi](icordebugboxvalue-interface.md)\
 `ICorDebugHeapValue`Paketlenmiş değer sınıf nesnesini temsil eden öğesinin alt sınıfı.  
  
 [ICorDebugBreakpoint arabirimi](icordebugbreakpoint-interface.md)\
 Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.  
  
 [ICorDebugBreakpointEnum arabirimi](icordebugbreakpointenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugBreakpoint` .  
  
 [Icordebugzincirine yönelik arabirim](icordebugchain-interface.md)\
 Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.  
  
 [ICorDebugChainEnum arabirimi](icordebugchainenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugChain` .  
  
 [ICorDebugClass arabirimi](icordebugclass-interface.md)\
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür geneldir ise, `ICorDebugClass` örneklenmemiş genel türü temsil eder.  
  
 [ICorDebugClass2 Arabirimi](icordebugclass2-interface.md)\
 Bir genel sınıfı veya türünde bir yöntem parametresi olan bir sınıfı temsil eder <xref:System.Type> . Bu arabirim genişletilir `ICorDebugClass` .  
  
 [ICorDebugCode arabirimi](icordebugcode-interface1.md)\
 Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
 [ICorDebugCode2 arabirimi](icordebugcode2-interface.md)\
 , Yeteneklerini genişleten yöntemler sağlar `ICorDebugCode` .  
  
 [ICorDebugCode3 Arabirimi](icordebugcode3-interface.md)\
 Yönetilen bir dönüş değeri hakkında bilgi sağlamak için [ICorDebugCode](icordebugcode-interface1.md) ve [ICorDebugCode2](icordebugcode2-interface.md) genişleten bir yöntem sağlar.  
  
 [ICorDebugCode4 arabirimi](icordebugcode4-interface.md)\
 Bir işlevdeki yerel değişkenleri ve bağımsız değişkenleri numaralandırmak için hata ayıklayıcı sağlayan bir yöntem sağlar.  
  
 [ICorDebugCodeEnum arabirimi](icordebugcodeenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugCode` .  
  
 [ICorDebugComObjectValue arabirimi](icordebugcomobjectvalue-interface.md)\
 Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.  
  
 [ICorDebugContext arabirimi](icordebugcontext-interface.md)\
 Bir bağlam nesnesini temsil eder. Bu arabirim henüz uygulanmamış.  
  
 [ICorDebugController arabirimi](icordebugcontroller-interface.md)\
 <xref:System.Diagnostics.Process> <xref:System.AppDomain> Kod yürütme bağlamının denetlenebileceği bir ya da olan bir kapsamı temsil eder.  
  
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
  
 [Icorıncertificate Geval arabirimi](icordebugeval-interface.md)\
 Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.  
  
 [ICorDebugEval2 arabirimi](icordebugeval2-interface.md)\
 `ICorDebugEval`Genel türler için destek sağlamak üzere genişletilir.  
  
 [Icordebugexceptiondebugger gevent arabirimi](icordebugexceptiondebugevent-interface.md)\
 Özel durum olaylarını desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugExceptionObjectCallStackEnum arabirimi](icordebugexceptionobjectcallstackenum-interface.md)\
 Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.  
  
 [ICorDebugExceptionObjectValue Arabirimi](icordebugexceptionobjectvalue-interface.md)\
 Yönetilen bir özel durum nesnesinden yığın izleme bilgisi sağlamak için [ICorDebugObjectValue](icordebugobjectvalue-interface.md) arabirimini genişletir.  
  
 [ICorDebugFrame arabirimi](icordebugframe-interface.md)\
 Geçerli yığındaki bir çerçeveyi temsil eder.  
  
 [ICorDebugFrameEnum arabirimi](icordebugframeenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugFrame` .  
  
 [ICorDebugFunction Arabirimi](icordebugfunction-interface1.md)\
 Yönetilen bir işlevi veya yöntemi temsil eder.  
  
 [ICorDebugFunction2 arabirimi](icordebugfunction2-interface.md)\
 `ICorDebugFunction`Yalnızca kendi kodum adım adım hata ayıklama için destek sağlamak üzere mantıksal olarak genişletilir.  
  
 [ICorDebugFunction3 arabirimi](icordebugfunction3-interface.md)\
 Bir ReJIT isteğinden koda erişim sağlamak için [ICorDebugFunction](icordebugfunction-interface1.md) arabirimini mantıksal olarak genişletir.  
  
 [ICorDebugFunctionBreakpoint Arabirimi](icordebugfunctionbreakpoint-interface.md)\
 `ICorDebugBreakpoint`İşlevleri içindeki kesme noktalarını destekleyecek şekilde genişletir.  
  
 [Icorıtcggcreferenceenum arabirimi](icordebuggcreferenceenum-interface.md)\
 Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.  
  
 [ICorDebugGenericValue arabirimi](icordebuggenericvalue-interface.md)\
 `ICorDebugValue`Tüm değerler için geçerli olan öğesinin bir alt sınıfı. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
 [ICorDebugGuidToTypeEnum arabirimi](icordebugguidtotypeenum-interface.md)\
 GUID 'Leri ve bunlara karşılık gelen nesnelerini eşleyen bir nesne için bir Numaralandırıcı sağlar `ICorDebugType` .  
  
 [Icorıınfo Ghandtavalue arabirimi](icordebughandlevalue-interface.md)\
 `ICorDebugReferenceValue`Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden öğesinin alt sınıfı.  
  
 [ICorDebugHeapEnum arabirimi](icordebugheapenum-interface.md)\
 Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.  
  
 [ICorDebugHeapSegmentEnum arabirimi](icordebugheapsegmentenum-interface.md)\
 Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.  
  
 [ICorDebugHeapValue Arabirimi](icordebugheapvalue-interface.md)\
 `ICorDebugValue`Clr çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eden öğesinin alt sınıfı.  
  
 [ICorDebugHeapValue2 arabirimi](icordebugheapvalue2-interface1.md)\
 `ICorDebugHeapValue`Çalışma zamanı tutamaçları için destek sağlayan uzantısı.  
  
 [ICorDebugHeapValue3 arabirimi](icordebugheapvalue3-interface.md)\
 Nesnelerin monitör kilit özelliklerini gösterir.  
  
 [ICorDebugILCode arabirimi](icordebugilcode-interface.md)\
 Ara dil (IL) kodu segmentini temsil eder.  
  
 [ICorDebugILCode2 arabirimi](icordebugilcode2-interface.md)\
 Bir işlevin yerel değişken imzasının belirtecini döndüren ve bir profiler 'ın belgelenmiş ara dili (IL) orijinal Yöntem Il uzaklıklarına eşleyen Yöntemler sağlamak için [ICorDebugILCode](icordebugilcode-interface.md) arabirimini mantıksal olarak genişletir.  
  
 [ICorDebugILFrame Arabirimi](icordebugilframe-interface.md)\
 MSIL kodunun bir yığın çerçevesini temsil eder.  
  
 [ICorDebugILFrame2 Arabirimi](icordebugilframe2-interface.md)\
 Öğesinin mantıksal uzantısı `ICorDebugILFrame` .  
  
 [ICorDebugILFrame3 arabirimi](icordebugilframe3-interface.md)\
 İşlevin dönüş değerini içeren bir yöntem sağlar.  
  
 [ICorDebugILFrame4 arabirimi](icordebugilframe4-interface.md)\
 Ara dil (IL) kodunun yığın çerçevesindeki yerel değişkenlere ve koda erişmenize imkan tanıyan yöntemler sağlar. Bir parametre, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere ve koda erişip erişemeyeceğini belirtir.  
  
 [Icordebugınstancefieldsymbol arabirimi](icordebuginstancefieldsymbol-interface.md)\
 Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugInternalFrame arabirimi](icordebuginternalframe-interface.md)\
 Hata ayıklayıcı için çerçeve türlerini tanımlar.  
  
 [ICorDebugInternalFrame2 Arabirimi](icordebuginternalframe2-interface.md)\
 Yığın adresi ve [ICorDebugFrame](icordebugframe-interface.md) nesneleriyle ilişkili konum dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.  
  
 [ICorDebugLoadedModule arabirimi](icordebugloadedmodule-interface.md)\
 Yüklü bir modül hakkında bilgi sağlar. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugManagedCallback arabirimi](icordebugmanagedcallback-interface.md)\
 Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.  
  
 [ICorDebugManagedCallback2 arabirimi](icordebugmanagedcallback2-interface.md)\
 Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar. `ICorDebugManagedCallback2` , öğesinin bir mantıksal uzantısıdır `ICorDebugManagedCallback` .  
  
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
 , İçin bir mantıksal uzantı görevi görür `ICorDebugModule` .  
  
 [ICorDebugModule3 Arabirimi](icordebugmodule3-interface.md)\
 Dinamik modül için simge okuyucu oluşturur.  
  
 [ICorDebugModuleBreakpoint arabirimi](icordebugmodulebreakpoint-interface.md)\
 `ICorDebugBreakpoint`Belirli modüllere erişim sağlamak için genişletir.  
  
 [Icordebugmoduledebugger gevent arabirimi](icordebugmoduledebugevent-interface.md)\
 Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugModuleEnum arabirimi](icordebugmoduleenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugModule` .  
  
 [Icordebugmutabledatatarget arabirimi](icordebugmutabledatatarget-interface.md)\
 [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini, değişebilir veri hedeflerini destekleyecek şekilde genişletir.  
  
 [ICorDebugNativeFrame arabirimi](icordebugnativeframe-interface.md)\
 `ICorDebugFrame`Yerel çerçeveler için kullanılan özel bir uygulama.  
  
 [ICorDebugNativeFrame2 arabirimi](icordebugnativeframe2-interface.md)\
 Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.  
  
 [ICorDebugObjectEnum arabirimi](icordebugobjectenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve bunlara göreli sanal adreslere göre nesne dizilerini numaralandırır (RVA).  
  
 [ICorDebugObjectValue arabirimi](icordebugobjectvalue-interface.md)\
 Bir `ICorDebugValue` nesnesi içeren bir değeri temsil eden öğesinin alt sınıfı.  
  
 [ICorDebugObjectValue2 arabirimi](icordebugobjectvalue2-interface.md)\
 `ICorDebugObjectValue`Devralma ve geçersiz kılmaları desteklemek için genişletir.  
  
 [ICorDebugProcess arabirimi](icordebugprocess-interface.md)\
 Yönetilen bir kodu yürüten bir işlemi temsil eder.  
  
 [ICorDebugProcess2 arabirimi](icordebugprocess2-interface1.md)\
 Öğesinin mantıksal uzantısı `ICorDebugProcess` .  
  
 [ICorDebugProcess3 arabirimi](icordebugprocess3-interface.md)\
 Özel hata ayıklayıcı bildirimlerini denetler.

 [ICorDebugProcess4 arabirimi](icordebugprocess4-interface.md)\
 İşlem dışı yürütme denetimi için destek sağlar.
  
 [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)\
 Yönetilen yığına erişimi desteklemek, yönetilen nesnelerin çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcının uygulamanın yerel yerel görüntü önbelleğinden görüntü yükleyip yükleyemeyeceğini anlamak için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini genişletir.  
  
 [ICorDebugProcess6 arabirimi](icordebugprocess6-interface.md)\
 Yerel özel durum ayıklama olayları ve sanal modül bölünmesi içinde kodlanmış yönetilen hata ayıklama olaylarının kodunu çözme gibi özellikleri etkinleştirmek için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini mantıksal olarak genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugProcess7 arabirimi](icordebugprocess7-interface.md)\
 Hata ayıklayıcıyı, hedef işlemdeki bellek içi meta veri güncelleştirmelerini işleyecek şekilde yapılandıran bir yöntem sağlar.  
  
 [ICorDebugProcess8 arabirimi](icordebugprocess8-interface.md)\
 Belirli [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) özel durum geri çağırmaları türlerini etkinleştirmek veya devre dışı bırakmak Için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini mantıksal olarak genişletir.  
  
 [ICorDebugProcessEnum arabirimi](icordebugprocessenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugProcess` .  
  
 [ICorDebugReferenceValue arabirimi](icordebugreferencevalue-interface.md)\
 Başvuru türlerini destekleyen öğesinin bir alt sınıfı `ICorDebugValue` .  
  
 [ICorDebugRegisterSet arabirimi](icordebugregisterset-interface.md)\
 Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.  
  
 [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)\
 `ICorDebugRegisterSet`64 ' den fazla kaydı olan donanım platformları için yeteneklerini genişletir.  
  
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
  
 [ICorDebugStepper Arabirimi](icordebugstepper-interface.md)\
 Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.  
  
 [ICorDebugStepper2 arabirimi](icordebugstepper2-interface1.md)\
 Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.  
  
 [ICorDebugStepperEnum arabirimi](icordebugstepperenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugStepper` .  
  
 [ICorDebugStringValue arabirimi](icordebugstringvalue-interface.md)\
 `ICorDebugHeapValue`Dize değerleri için geçerli olan alt sınıfı.  
  
 [ICorDebugSymbolProvider arabirimi](icordebugsymbolprovider-interface.md)\
 Hata ayıklama sembolü bilgilerini almak için kullanılabilecek yöntemler sağlar. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugSymbolProvider2 arabirimi](icordebugsymbolprovider2-interface.md)\
 Ek hata ayıklama sembol bilgilerini almak için [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) arabirimini mantıksal olarak genişletir. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugThread arabirimi](icordebugthread-interface.md)\
 Bir işlemdeki bir iş parçacığını temsil eder. Bir örneğin yaşam süresi, `ICorDebugThread` temsil ettiği iş parçacığının ömrü ile aynıdır.  
  
 [ICorDebugThread2 arabirimi](icordebugthread2-interface.md)\
 , İçin bir mantıksal uzantı görevi görür `ICorDebugThread` .  
  
 [ICorDebugThread3 Arabirimi](icordebugthread3-interface.md)\
 [Icordebugstackyürüme](icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.  
  
 [ICorDebugThread4 arabirimi](icordebugthread4-interface.md)\
 İş parçacığı engelleme bilgileri sağlar.  
  
 [ICorDebugThreadEnum arabirimi](icordebugthreadenum-interface1.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugThread` .  
  
 [ICorDebugType arabirimi](icordebugtype-interface.md)\
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür geneldir ise, `ICorDebugType` örneklenmiş genel türü temsil eder.  
  
 [ICorDebugType2 arabirimi](icordebugtype2-interface.md)\
 Bir temel türün tür tanımlayıcısını veya karmaşık (Kullanıcı tanımlı) türünü almak için [ICorDebugType](icordebugtype-interface.md) arabirimini genişletir.  
  
 [ICorDebugTypeEnum Arabirimi](icordebugtypeenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugType` .  
  
 [ICorDebugUnmanagedCallback arabirimi](icordebugunmanagedcallback-interface.md)\
 CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.  
  
 [ICorDebugValue](icordebugvalue-interface.md)\
 Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 `ICorDebugValue`İçin destek sağlamak üzere genişletilir `ICorDebugType` .  
  
 [ICorDebugValue3 arabirimi](icordebugvalue3-interface.md)\
 2 GB 'den büyük diziler için destek sağlamak üzere "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 `ICorDebugBreakpoint`Belirli değerlere erişim sağlamak için genişletir.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 `ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugValue` .  
  
 [Icordebugvariablehome arabirimi](icordebugvariablehome-interface.md)\
 Bir işlevin yerel bir değişkenini veya bağımsız değişkenini temsil eder.  
  
 [Icordebugvariablehomeenum arabirimi](icordebugvariablehomeenum-interface.md)\
 Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı sağlar.  
  
 [ICorDebugVariableSymbol arabirimi](icordebugvariablesymbol-interface.md)\
 Bir değişken için hata ayıklama sembol bilgisini alır. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorDebugVirtualUnwinder Arabirimi](icordebugvirtualunwinder-interface.md)\
 Yığın geri sarma konusunda yardımcı olmak için yöntemler sağlar. **Yalnızca .NET Native kullanılabilir.**  
  
 [ICorPublish arabirimi](icorpublish-interface.md)\
 Yayınlama işlevinin genel arabirimi olarak işlev görür.  
  
 [ICorPublishAppDomain arabirimi](icorpublishappdomain-interface.md)\
 Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.  
  
 [ICorPublishAppDomainEnum Arabirimi](icorpublishappdomainenum-interface.md)\
 `ICorPublishAppDomain`Bir işlem içinde mevcut olan nesnelerin bir koleksiyonunu gezme yöntemleri sağlar.  
  
 [ICorPublishEnum arabirimi](icorpublishenum-interface.md)\
 Numaralandırıcılar yayımlamak için soyut temel görevi görür.  
  
 [ICorPublishProcess arabirimi](icorpublishprocess-interface.md)\
 İşlemle ilgili bilgilere erişen yöntemler sağlar.  
  
 [ICorPublishProcessEnum arabirimi](icorpublishprocessenum-interface.md)\
 Bir nesne koleksiyonunu gezme yöntemleri sağlar `ICorPublishProcess` .  

 [Isosdacınterface arabirimi](isosdacinterface-interface.md)\
 Verilerine erişmek için yardımcı yöntemler sağlar `SOS` .

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
 [Hata ayıklama yapıları](debugging-structures.md)\
