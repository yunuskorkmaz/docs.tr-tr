---
title: Hata Ayıklama Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b6d00d17615769a5d03d58e0eda5af62ca58368
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415968"
---
# <a name="debugging-interfaces"></a>Hata Ayıklama Arabirimleri
Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ICLRDataEnumMemoryRegions Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.  
  
 [ICLRDataEnumMemoryRegionsCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 İçin bir geri arama yöntemi sağlar `EnumMemoryRegions` hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için.  
  
 [ICLRDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 Hedef CLR işlemiyle etkileşim için yöntemler sağlar.  
  
 [ICLRDataTarget2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 Öğesinin `ICLRDataTarget` , veri erişim Hizmetleri düzeyi tarafından hedef işlemde sanal bellek bölümlerini işlemek için kullanılır.  
  
 [ICLRDataTarget3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 Öğesinin [Iclrdatatarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , özel durum bilgilerine erişim sağlar.  
  
 [ICLRDebugging Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.  
  
 [ICLRDebuggingLibraryProvider Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 İçerir [ProvideLibrary yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) kitaplık sağlayıcı ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarına ve yüklenecek isteğe bağlı olmasını sağlayan bir geri arama arabirimini alan yöntemi.  
  
 [ICLRMetadataLocator Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.  
  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.  
  
 [ICorDebugAppDomain Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.  
  
 [ICorDebugAppDomain2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar. Bu arabirim uzantısıdır `ICorDebugAppDomain` arabirimi.  
  
 [ICorDebugAppDomain3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 Çalışmak için yöntemler sağlar [!INCLUDE[wrt](../../../../includes/wrt-md.md)] uygulama etki alanında türleri. Bu arabirim uzantısıdır `ICorDebugAppDomain` ve `ICorDebugAppDomain2` arabirimleri.  
  
 [ICorDebugAppDomain4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 Mantıksal olarak genişletir [Icordebugappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) COM çağrılabilir sarmalayıcısı yönetilen bir nesneye almak için arabirim.  
  
 [ICorDebugAppDomainEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 Belirtilen sayıda döndüren bir yöntem sağlar `ICorDebugAppDomain` sonraki konumdan başlayarak değerleri.  
  
 [ICorDebugArrayValue Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 Öğesinin `ICorDebugHeapValue` temsil eden tek boyutlu veya çok boyutlu bir dizi.  
  
 [ICorDebugAssembly Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 Bir derlemeyi temsil eder.  
  
 [ICorDebugAssembly2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 Bir derlemeyi temsil eder. Bu arabirim uzantısıdır `ICorDebugAssembly` arabirimi.  
  
 [ICorDebugAssembly3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 Mantıksal olarak genişletir [Icordebugassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) kapsayıcı derlemeleri ve bunların içerdiği derlemeleri için destek sağlamak için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugAssemblyEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugAssembly` dizileri.  
  
 [ICorDebugBlockingObjectEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 Bir listesi için bir numaralandırıcı sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.  
  
 [ICorDebugBoxValue Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 Öğesinin `ICorDebugHeapValue` paketlenmiş değer sınıf nesnesini temsil eden.  
  
 [ICorDebugBreakpoint Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.  
  
 [ICorDebugBreakpointEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugBreakpoint` dizileri.  
  
 [ICorDebugChain Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.  
  
 [ICorDebugChainEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugChain` dizileri.  
  
 [ICorDebugClass Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür genelse, `ICorDebugClass` örneklenmemiş genel türü temsil eder.  
  
 [ICorDebugClass2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 Genel bir sınıf veya türündeki bir yöntem parametresi olan bir sınıfı temsil eden <xref:System.Type>. Bu arabirim genişletir `ICorDebugClass`.  
  
 [ICorDebugCode Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
 [ICorDebugCode2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 Özelliklerini genişleten yöntemler sağlar `ICorDebugCode`.  
  
 [ICorDebugCode3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 Genişleten bir yöntem sağlar [Icordebugcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) ve [Icordebugcode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) yönetilen bir dönüş değeri hakkında bilgi sağlamak için.  
  
 [ICorDebugCode4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 Bir işlevdeki bağımsız değişkenler ve yerel değişkenler numaralandırmak bir hata ayıklayıcı sağlayan bir yöntem sağlar.  
  
 [ICorDebugCodeEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugCode` dizileri.  
  
 [ICorDebugComObjectValue Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.  
  
 [ICorDebugContext Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 Bir bağlam nesnesini temsil eder. Bu arabirim henüz uygulanmamış.  
  
 [ICorDebugController Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 Bir kapsamı temsil eder bir <xref:System.Diagnostics.Process> veya <xref:System.AppDomain>, hangi kod yürütme bağlamının denetlenebileceği.  
  
 [ICorDebugDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.  
  
 [ICorDebugDataTarget2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugDataTarget3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) yüklü modülleri hakkında bilgi sağlamak için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugDebugEvent Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olaylarını türetilir. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugEditAndContinueErrorInfo Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [ICorDebugEditAndContinueSnapshot Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [ICorDebugEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.  
  
 [ICorDebugErrorInfoEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [ICorDebugEval Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.  
  
 [ICorDebugEval2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 Genişletir `ICorDebugEval` genel türler için destek sağlamak için.  
  
 [ICorDebugExceptionDebugEvent Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) özel durum olaylarının desteklemek için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugExceptionObjectCallStackEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.  
  
 [ICorDebugExceptionObjectValue Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 Genişletir [Icordebugobjectvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) bir yönetilen özel durum nesnesinden yığın izleme bilgisi sağlamak için arabirim.  
  
 [ICorDebugFrame Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 Geçerli yığındaki bir çerçeveyi temsil eder.  
  
 [ICorDebugFrameEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugFrame` dizileri.  
  
 [ICorDebugFunction Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 Yönetilen bir işlevi veya yöntemi temsil eder.  
  
 [ICorDebugFunction2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 Mantıksal olarak genişletir `ICorDebugFunction` yalnızca kendi kodum adım adım hata ayıklama için destek sağlamak için.  
  
 [ICorDebugFunction3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 Mantıksal olarak genişletir [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) ReJIT istekten koda erişim sağlamak için arabirim.  
  
 [ICorDebugFunctionBreakpoint Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 Genişletir `ICorDebugBreakpoint` işlevlerdeki kesme noktalarını desteklemek için.  
  
 [ICorDebugGCReferenceEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.  
  
 [ICorDebugGenericValue Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 Öğesinin `ICorDebugValue` tüm değerlere uygulanır. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
 [ICorDebugGuidToTypeEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 Bunlara karşılık gelen eşleyen nesne için bir numaralandırıcı sağlar `ICorDebugType` nesneleri.  
  
 [ICorDebugHandleValue Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 Öğesinin `ICorDebugReferenceValue` için hata ayıklayıcı çöp toplama işlemi için bir tanıtıcı oluşturduğu bir başvuru değeri temsil eder.  
  
 [ICorDebugHeapEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.  
  
 [ICorDebugHeapSegmentEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.  
  
 [ICorDebugHeapValue Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 Öğesinin `ICorDebugValue` CLR çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eder.  
  
 [ICorDebugHeapValue2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 ' In bir uzantısı `ICorDebugHeapValue` , çalışma zamanı işleçlerine ilişkin destek sağlar.  
  
 [ICorDebugHeapValue3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 Nesnelerin monitör kilit özelliklerini gösterir.  
  
 [ICorDebugILCode Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 Ara dil (IL) kodu kesimini temsil eder.  
  
 [ICorDebugILCode2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 Mantıksal olarak genişletir [Icordebugılcode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) yönelik bir işlevin yerel değişken imzası belirtecini döndürür ve bir profil oluşturucunun Araçlı Ara dil (IL) map yöntemleri sağlamak için arabirimi kaydırır IL özgün yöntemi kaydırır.  
  
 [ICorDebugILFrame Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 MSIL kodunun bir yığın çerçevesini temsil eder.  
  
 [ICorDebugILFrame2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 Öğesinin mantıksal uzantısı `ICorDebugILFrame`.  
  
 [ICorDebugILFrame3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 İşlevin dönüş değerini içeren bir yöntem sağlar.  
  
 [ICorDebugILFrame4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 Yerel değişkenleri ve Ara dil (IL) kodu bir yığın çerçevesi kodu erişim olanak tanıyan yöntemler sağlar. Bir parametre, hata ayıklayıcı değişkenleri ve ReJIT izleme profil oluşturucu, eklenen kod erişimi olup olmadığını belirtir.  
  
 [ICorDebugInstanceFieldSymbol Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 Bir örnek alanıyla hata ayıklama sembolü bilgilerini temsil eder. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugInternalFrame Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 Hata ayıklayıcı için çerçeve türlerini tanımlar.  
  
 [ICorDebugInternalFrame2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 Yığın adresi ve ilişkili olarak dahil olmak üzere, iç çerçeveler hakkında bilgi sağlar [Icordebugframe](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) nesneleri.  
  
 [ICorDebugLoadedModule Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 Yüklenen bir modülün hakkında bilgi sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.  
  
 [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar. `ICorDebugManagedCallback2` öğesinin mantıksal uzantısıdır `ICorDebugManagedCallback`.  
  
 [ICorDebugManagedCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.  
  
 [ICorDebugMDA Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.  
  
 [ICorDebugMemoryBuffer Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 Bir bellek arabelleğini temsil eder. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugMergedAssemblyRecord Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 Birleştirilmiş bir derleme hakkında bilgi sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugMetaDataLocator Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 Hata ayıklayıcıya meta veri bilgileri sağlar.  
  
 [ICorDebugModule Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.  
  
 [ICorDebugModule2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 Bir mantıksal uzantısı olarak işlev görür `ICorDebugModule`.  
  
 [ICorDebugModule3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 Dinamik modül için simge okuyucu oluşturur.  
  
 [ICorDebugModuleBreakpoint Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 Genişletir `ICorDebugBreakpoint` belirli modüllere erişim sağlamak için.  
  
 [ICorDebugModuleDebugEvent Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) Modül düzeyinde olaylar desteklemek için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugModuleEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugModule` dizileri.  
  
 [ICorDebugMutableDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 Genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.  
  
 [ICorDebugNativeFrame Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 Öğesinin özelleşmiş uygulaması `ICorDebugFrame` yerel çerçeveler için kullanılır.  
  
 [ICorDebugNativeFrame2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.  
  
 [ICorDebugObjectEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve bunların göreli sanal adreslerine (RVA) göre nesne dizilerini numaralandırır.  
  
 [ICorDebugObjectValue Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 Öğesinin `ICorDebugValue` temsil eden bir nesne içeren bir değer.  
  
 [ICorDebugObjectValue2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 Genişletir `ICorDebugObjectValue` devralma ve geçersiz kılmaları desteklemek için.  
  
 [ICorDebugProcess Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 Yönetilen bir kodu yürüten bir işlemi temsil eder.  
  
 [ICorDebugProcess2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 Öğesinin mantıksal uzantısı `ICorDebugProcess`.  
  
 [ICorDebugProcess3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 Özel hata ayıklayıcı bildirimlerini denetler.  
  
 [ICorDebugProcess5 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 Genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) yerel, yönetilen nesnelerin Çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcı uygulamadan görüntüleri yükleyip yüklemediğini belirlemek için yönetilen yığına erişimi desteklemek için arabirimi Yerel görüntü önbelleği.  
  
 [ICorDebugProcess6 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 Mantıksal olarak genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) yerel özel durum hata ayıklama olaylarını ve sanal modül bölme kodlanmış yönetilen hata ayıklama olaylarını kod çözme gibi özellikleri etkinleştirmek için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugProcess7 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 Hedef işlem, bellek içi meta veri güncelleştirmeleri işlemek için hata ayıklayıcı yapılandıran bir yöntem sağlar.  
  
 [ICorDebugProcess8 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 Mantıksal olarak genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) etkinleştirme veya devre dışı belirli türlerdeki arabirimi [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) özel durum geri aramalarını.  
  
 [ICorDebugProcessEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugProcess` dizileri.  
  
 [ICorDebugReferenceValue Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 Öğesinin `ICorDebugValue` başvuru türlerini destekler.  
  
 [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.  
  
 [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 Yeteneklerini genişletir `ICorDebugRegisterSet` 64'den fazla kayda sahip donanım platformları için.  
  
 [ICorDebugRemote Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.  
  
 [ICorDebugRemoteTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.  
  
 [ICorDebugRuntimeUnwindableFrame Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.  
  
 [ICorDebugStackWalk Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.  
  
 [ICorDebugStaticFieldSymbol Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 Statik bir alan için hata ayıklama bilgilerini temsil eder. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugStepper Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.  
  
 [ICorDebugStepper2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.  
  
 [ICorDebugStepperEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugStepper` dizileri.  
  
 [ICorDebugStringValue Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 Öğesinin `ICorDebugHeapValue` dize değerleri için geçerlidir.  
  
 [ICorDebugSymbolProvider Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 Hata ayıklama bilgilerini almak için kullanılan yöntemler sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugSymbolProvider2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 Mantıksal olarak genişletir [Icordebugsymbolprovider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) ek hata ayıklama bilgilerini almak için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugThread Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 Bir işlemdeki bir iş parçacığını temsil eder. Yaşam süresi bir `ICorDebugThread` örneğidir ömrü, temsil ettiği iş parçacığı ile aynı.  
  
 [ICorDebugThread2 Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 Bir mantıksal uzantısı olarak işlev görür `ICorDebugThread`.  
  
 [ICorDebugThread3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 Giriş noktası sağlar [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve karşılık gelen arabirimleri.  
  
 [ICorDebugThread4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 İş parçacığı engelleme bilgileri sağlar.  
  
 [ICorDebugThreadEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugThread` dizileri.  
  
 [ICorDebugType Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür genelse, `ICorDebugType` örneklenmiş genel türü temsil eder.  
  
 [ICorDebugType2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 Genişletir [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) türü tanımlayıcısı bir temel türü veya karmaşık türü (kullanıcı tanımlı) almak için arabirim.  
  
 [ICorDebugTypeEnum Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugType` dizileri.  
  
 [ICorDebugUnmanagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.  
  
 "ICorDebugValue"  
 Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.  
  
 "ICorDebugValue2"  
 Genişletir `ICorDebugValue` için destek sağlamak üzere `ICorDebugType`.  
  
 [ICorDebugValue3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 2 GB'den daha büyük diziler için destek sağlamak için "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.  
  
 "ICorDebugValueBreakpoint"  
 Genişletir `ICorDebugBreakpoint` belirli değerlere erişim sağlamak için.  
  
 "ICorDebugValueEnum"  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugValue` dizileri.  
  
 [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 Bir yerel değişken veya işlev bağımsız değişkeni temsil eder.  
  
 [ICorDebugVariableHomeEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 Bir işlevdeki bağımsız değişkenler ve yerel değişkenler için bir numaralandırıcı sağlar.  
  
 [ICorDebugVariableSymbol Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 Bir değişken için hata ayıklama bilgilerini alır. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugVirtualUnwinder Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 Yığın geriye doğru izleme yardımcı olmak için yöntemleri sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorPublish Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 Yayınlama işlevinin genel arabirimi olarak işlev görür.  
  
 [ICorPublishAppDomain Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.  
  
 [ICorPublishAppDomainEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 Koleksiyonunu geçirmek için yöntemler sağlar `ICorPublishAppDomain` şu anda bir işlem içinde varolan nesneleri.  
  
 [ICorPublishEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 Numaralandırıcılar yayımlamak için soyut temel görevi görür.  
  
 [ICorPublishProcess Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 İşlemle ilgili bilgilere erişen yöntemler sağlar.  
  
 [ICorPublishProcessEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 Koleksiyonunu geçirmek için yöntemler sağlar `ICorPublishProcess` nesneleri.  

 [ISOSDacInterface arabirimi](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) verilere erişmek için yardımcı yöntemleri sağlar `SOS`.

 [IXCLRDataMethodDefinition arabirimi](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) yöntemi tanımı hakkında bilgi sorgulamak için yöntemler sağlar.
 
 [IXCLRDataMethodInstance arabirimi](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) metot örneği hakkında bilgi sorgulamak için yöntemler sağlar.
 
 [IXCLRDataModule arabirimi](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) yüklenen bir modülün hakkında bilgi sorgulamak için yöntemler sağlar.
 
 [IXCLRDataProcess arabirimi](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) bir işlem hakkında bilgi sorgulamak için yöntemler sağlar.
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Coclass’ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
