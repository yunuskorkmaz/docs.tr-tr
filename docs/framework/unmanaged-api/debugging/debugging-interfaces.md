---
title: "Hata Ayıklama Arabirimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de2469d15eef40b9ef283d67aeca429d9d96a7ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-interfaces"></a>Hata Ayıklama Arabirimleri
Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Iclrdataenummemoryregions arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.  
  
 [Iclrdataenummemoryregionscallback arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 Bir geri arama yöntemi sağlar `EnumMemoryRegions` hata ayıklayıcı belirtilen bölge bellek numaralandırılamıyor girişiminde sonucunu bildirilecek.  
  
 [Iclrdatatarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 Hedef CLR işlemiyle etkileşim için yöntemler sağlar.  
  
 [Iclrdatatarget2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 Öğesinin bir alt `ICLRDataTarget` , veri erişim Hizmetleri katmanı tarafından hedef işlem sanal bellek bölgelerde işlemek için kullanılır.  
  
 [Iclrdatatarget3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 Öğesinin bir alt [Iclrdatatarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) özel durum bilgilerine erişim sağlar.  
  
 [Iclrdebugging arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.  
  
 [Iclrdebugginglibraryprovider arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 İçeren [ProvideLibrary yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) ortak dil çalışma zamanı sürüme özgü hata ayıklama kitaplıkları bulunduğu ve yüklenen üzerinde isteğe bağlı olarak geri çağırma arabirimi kitaplığı sağlayıcısını alır yöntemi.  
  
 [Iclrmetadatalocator arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.  
  
 [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.  
  
 [Icordebugappdomain Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.  
  
 [Icordebugappdomain2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar. Bu arabirim uzantısıdır `ICorDebugAppDomain` arabirimi.  
  
 [Icordebugappdomain3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 Çalışmak için yöntemler sağlar [!INCLUDE[wrt](../../../../includes/wrt-md.md)] uygulama etki alanı türleri. Bu arabirim uzantısıdır `ICorDebugAppDomain` ve `ICorDebugAppDomain2` arabirimleri.  
  
 [Icordebugappdomain4 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 Mantıksal olarak genişletir [Icordebugappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) COM aranabilir sarmalayıcısı yönetilen bir nesnenin almak için arabirim.  
  
 [Icordebugappdomainenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 Belirtilen sayıda döndüren bir yöntem sağlar `ICorDebugAppDomain` listedeki sonraki konumunda başlayan değer.  
  
 [Icordebugarrayvalue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 Öğesinin bir alt `ICorDebugHeapValue` temsil eden bir tek boyutlu veya çok boyutlu dizi.  
  
 [Icordebugassembly Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 Bir derlemeyi temsil eder.  
  
 [Icordebugassembly2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 Bir derlemeyi temsil eder. Bu arabirim uzantısıdır `ICorDebugAssembly` arabirimi.  
  
 [Icordebugassembly3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 Mantıksal olarak genişletir [Icordebugassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) kapsayıcı derlemeler ve bunların içerdiği derlemeler için destek sağlamak için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugassemblyenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugAssembly` dizileri.  
  
 [Icordebugblockingobjectenum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 Bir listesi için bir numaralandırıcı sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.  
  
 [Icordebugboxvalue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 Öğesinin bir alt `ICorDebugHeapValue` paketlenmiş değer sınıf nesnesini temsil eden.  
  
 [Icordebugbreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.  
  
 [Icordebugbreakpointenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugBreakpoint` dizileri.  
  
 [Icordebugchain Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.  
  
 [Icordebugchainenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugChain` dizileri.  
  
 [Icordebugclass Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür genel, ise `ICorDebugClass` dizilerine genel türünü temsil eder.  
  
 [Icordebugclass2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 Genel bir sınıf veya yöntemi parametresi ile bir sınıf türü temsil eden <xref:System.Type>. Bu arabirim genişletir `ICorDebugClass`.  
  
 [Icordebugcode Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
 [Icordebugcode2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 Yeteneklerini yöntemleri sağlayan `ICorDebugCode`.  
  
 [Icordebugcode3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 Genişleten bir yöntem sağlar [Icordebugcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) ve [Icordebugcode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) yönetilen dönüş değeri hakkında bilgi sağlamak için.  
  
 [ICorDebugCode4 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 Yerel değişkenleri ve bir işlev bağımsız değişkenleri numaralandırmak bir hata ayıklayıcısı sağlayan bir yöntem sağlar.  
  
 [Icordebugcodeenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugCode` dizileri.  
  
 [Icordebugcomobjectvalue arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.  
  
 [Icordebugcontext Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 Bir bağlam nesnesini temsil eder. Bu arabirim henüz uygulanmamış.  
  
 [Icordebugcontroller Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 Bir kapsamı ya da temsil eden bir <xref:System.Diagnostics.Process> veya bir <xref:System.AppDomain>, hangi kod yürütme bağlamı denetlenebilir.  
  
 [Icordebugdatatarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.  
  
 [Icordebugdatatarget2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugdatatarget3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) yüklü modüller hakkında bilgi sağlamak için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugdebugevent arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olayları türetilir. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugeditandcontinueerrorınfo arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [Icordebugeditandcontinuesnapshot Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [Icordebugenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.  
  
 [Icordebugerrorınfoenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 Kullanımdan kalktı. Bu arayüzü kullanmayın.  
  
 [Icordebugeval Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.  
  
 [Icordebugeval2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 Genişletir `ICorDebugEval` genel türleri için destek sağlamak için.  
  
 [Icordebugexceptiondebugevent arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) özel durum olayları desteklemek için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugexceptionobjectcallstackenum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.  
  
 [Icordebugexceptionobjectvalue arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 Genişletir [Icordebugobjectvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) yönetilen özel durum nesnesinden yığın izleme bilgileri sağlamak için arabirim.  
  
 [Icordebugframe Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 Geçerli yığındaki bir çerçeveyi temsil eder.  
  
 [Icordebugframeenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugFrame` dizileri.  
  
 [ICorDebugFunction Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 Yönetilen bir işlevi veya yöntemi temsil eder.  
  
 [Icordebugfunction2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 Mantıksal olarak genişletir `ICorDebugFunction` sadece kendi kodumu adımla hata ayıklama için destek sağlamak için.  
  
 [Icordebugfunction3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 Mantıksal olarak genişletir [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) ReJIT isteğinden koduna erişim sağlamak için arabirim.  
  
 [Icordebugfunctionbreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 Genişletir `ICorDebugBreakpoint` kesme noktaları işlevler içinde desteklemek için.  
  
 [Icordebuggcreferenceenum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.  
  
 [Icordebuggenericvalue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 Öğesinin bir alt `ICorDebugValue` tüm değerleri için geçerlidir. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
 [Icordebugguidtotypeenum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 GUID ve karşılık gelen eşleyen bir nesne için bir numaralandırıcı sağlar `ICorDebugType` nesneleri.  
  
 [Icordebughandlevalue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 Öğesinin bir alt `ICorDebugReferenceValue` için hata ayıklayıcı çöp toplama için bir tanıtıcı oluşturduğu başvuru değeri temsil eder.  
  
 [Icordebugheapenum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.  
  
 [Icordebugheapsegmentenum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.  
  
 [Icordebugheapvalue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 Öğesinin bir alt `ICorDebugValue` CLR atık toplayıcısı tarafından toplanan nesneyi temsil eder.  
  
 [Icordebugheapvalue2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 Bir uzantısı olarak `ICorDebugHeapValue` çalışma zamanı tanıtıcıları için destek sağlar.  
  
 [Icordebugheapvalue3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 Nesnelerin monitör kilit özelliklerini gösterir.  
  
 [Icordebugılcode arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 Ara dile (IL) kod kesimi temsil eder.  
  
 [Icordebugılcode2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 Mantıksal olarak genişletir [Icordebugılcode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) bir işlevin yerel değişken imza için belirteci dönün ve Profil Oluşturucu'nın Araçlı Ara dile (IL) eşleme yöntemlerini sağlamak üzere arabirimi kaydırır IL özgün yöntemi kaydırır.  
  
 [Icordebugılframe Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 MSIL kodunun bir yığın çerçevesini temsil eder.  
  
 [Icordebugılframe2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 Mantıksal bir uzantısı `ICorDebugILFrame`.  
  
 [Icordebugılframe3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 İşlevin dönüş değerini içeren bir yöntem sağlar.  
  
 [Icordebugılframe4 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 Yerel değişkenleri ve Ara dile (IL) kodunun yığın çerçevesi kodda erişmenize olanak sağlayan yöntemleri sağlar. Bir parametre hata ayıklayıcı değişkenleri ve profiler ReJIT araçları eklenen kod erişim sahip olup olmadığını belirtir.  
  
 [ICorDebugInstanceFieldSymbol arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 Bir örnek alanındaki hata ayıklama sembol bilgilerini temsil eder. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugınternalframe Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 Hata ayıklayıcı için çerçeve türlerini tanımlar.  
  
 [Icordebugınternalframe2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 Yığın adresi ve yazılımla ilişkili olarak konumu gibi iç çerçeveler hakkında bilgiler sağlar [Icordebugframe](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) nesneleri.  
  
 [Icordebugloadedmodule arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 Yüklenen modülü hakkında bilgi sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugmanagedcallback arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.  
  
 [Icordebugmanagedcallback2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar. `ICorDebugManagedCallback2`mantıksal bir uzantısıdır ve `ICorDebugManagedCallback`.  
  
 [Icordebugmanagedcallback3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.  
  
 [Icordebugmda arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.  
  
 [ICorDebugMemoryBuffer arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 Bir bellek içi arabellek temsil eder. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugMergedAssemblyRecord arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 Birleştirilmiş bir derleme hakkında bilgi sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugmetadatalocator arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 Hata ayıklayıcıya meta veri bilgileri sağlar.  
  
 [Icordebugmodule Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.  
  
 [Icordebugmodule2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 Mantıksal bir uzantısı olarak hizmet veren `ICorDebugModule`.  
  
 [Icordebugmodule3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 Dinamik modül için simge okuyucu oluşturur.  
  
 [Icordebugmodulebreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 Genişletir `ICorDebugBreakpoint` belirli modüller erişim sağlamak için.  
  
 [ICorDebugModuleDebugEvent arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) modül düzeyi olaylarını desteklemek için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugmoduleenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugModule` dizileri.  
  
 [ICorDebugMutableDataTarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 Genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.  
  
 [Icordebugnativeframe Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 Özelleştirilmiş bir uyarlamasını `ICorDebugFrame` yerel çerçeveler için kullanılır.  
  
 [Icordebugnativeframe2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.  
  
 [Icordebugobjectenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve bunların göreli sanal adresler (RVAs) tarafından nesne dizileri numaralandırır.  
  
 [Icordebugobjectvalue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 Öğesinin bir alt `ICorDebugValue` temsil eden bir nesne içeren bir değer.  
  
 [Icordebugobjectvalue2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 Genişletir `ICorDebugObjectValue` devralma ve geçersiz kılmalar desteklemek için.  
  
 [Icordebugprocess Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 Yönetilen bir kodu yürüten bir işlemi temsil eder.  
  
 [Icordebugprocess2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 Mantıksal bir uzantısı `ICorDebugProcess`.  
  
 [Icordebugprocess3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 Özel hata ayıklayıcı bildirimlerini denetler.  
  
 [Icordebugprocess5 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 Genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) Yönetilen yığın yönetilen nesnelerin çöp toplama hakkında bilgi sağlar ve bir hata ayıklayıcısı uygulamadan görüntüleri yükler olup olmadığını belirlemek için erişimi desteklemek için arabirim yerel Yerel görüntü önbelleği.  
  
 [Icordebugprocess6 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 Mantıksal olarak genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) yerel özel durum hata ayıklama olayları ve sanal modülü bölme kodlanmış yönetilen hata ayıklama olayları kod çözme gibi özellikleri etkinleştirmek için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugprocess7 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 Hedef işlemin bellek içi meta veri güncelleştirmeleri işlemek için hata ayıklayıcı yapılandırır bir yöntem sağlar.  
  
 [Icordebugprocess8 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 Mantıksal olarak genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) etkinleştirme veya devre dışı belirli türde bir arabirim [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) özel durum geri aramalar.  
  
 [Icordebugprocessenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugProcess` dizileri.  
  
 [Icordebugreferencevalue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 Öğesinin bir alt `ICorDebugValue` destekler türleri başvuru.  
  
 [Icordebugregisterset arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.  
  
 [Icordebugregisterset2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 Yeteneklerini genişletir `ICorDebugRegisterSet` 64 taneden fazla kayıtları olan donanım platformları için.  
  
 [Icordebugremote arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.  
  
 [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.  
  
 [Icordebugruntimeunwindableframe arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.  
  
 [Icordebugstackwalk arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.  
  
 [ICorDebugStaticFieldSymbol arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 Statik bir alana hata ayıklama sembol bilgilerini temsil eder. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugStepper Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.  
  
 [Icordebugstepper2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.  
  
 [Icordebugstepperenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugStepper` dizileri.  
  
 [Icordebugstringvalue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 Öğesinin bir alt `ICorDebugHeapValue` dize değerleri için geçerlidir.  
  
 [ICorDebugSymbolProvider arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 Hata ayıklama sembol bilgilerini almak için kullanılan yöntemleri sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [ICorDebugSymbolProvider2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 Mantıksal olarak genişletir [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) ek hata ayıklama sembol bilgilerini almak için arabirim. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugthread Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 Bir işlemdeki bir iş parçacığını temsil eder. Yaşam süresi bir `ICorDebugThread` örneğidir temsil ettiği iş parçacığı ömrü ile aynı.  
  
 [Icordebugthread2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 Mantıksal bir uzantısı olarak hizmet veren `ICorDebugThread`.  
  
 [Icordebugthread3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 Giriş noktası sağlar [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve karşılık gelen arabirimler.  
  
 [Icordebugthread4 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 İş parçacığı engelleme bilgileri sağlar.  
  
 [Icordebugthreadenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugThread` dizileri.  
  
 [Icordebugtype Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür genel, ise `ICorDebugType` oluşturulmuş genel türünü temsil eder.  
  
 [ICorDebugType2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 Genişletir [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) arabirimi bir temel veya karmaşık türü (kullanıcı tanımlı) türü tanıtıcısı alınamadı.  
  
 [Icordebugtypeenum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugType` dizileri.  
  
 [Icordebugunmanagedcallback arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.  
  
 "ICorDebugValue"  
 Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.  
  
 "ICorDebugValue2"  
 Genişletir `ICorDebugValue` desteği sağlamak üzere `ICorDebugType`.  
  
 [Icordebugvalue3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 2 GB'den daha büyük boyutlu diziler için destek sağlamak için "ICorDebugValue" ve "ICorDebugValue2" arabirimleri genişletir.  
  
 "ICorDebugValueBreakpoint"  
 Genişletir `ICorDebugBreakpoint` belirli değerleri erişim sağlamak için.  
  
 "ICorDebugValueEnum"  
 Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugValue` dizileri.  
  
 [ICorDebugVariableHome arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 Yerel bir değişken veya işlev bağımsız değişkeni temsil eder.  
  
 [ICorDebugVariableHomeEnum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 Yerel değişkenleri ve bir işlev bağımsız değişkenleri için bir numaralandırıcı sağlar.  
  
 [ICorDebugVariableSymbol arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 Bir değişken için hata ayıklama sembol bilgileri alır. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icordebugvirtualunwinder arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 Yığın geriye doğru izleme yardımcı olmak için yöntemleri sağlar. **Yalnızca .NET yerel kullanılabilir.**  
  
 [Icorpublish arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 Yayınlama işlevinin genel arabirimi olarak işlev görür.  
  
 [Icorpublishappdomain arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.  
  
 [Icorpublishappdomainenum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 Bir koleksiyonu çapraz yöntemleri sağlar `ICorPublishAppDomain` şu anda bir işlem içinde mevcut nesneleri.  
  
 [Icorpublishenum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 Numaralandırıcılar yayımlamak için soyut temel görevi görür.  
  
 [Icorpublishprocess arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 İşlemle ilgili bilgilere erişen yöntemler sağlar.  
  
 [Icorpublishprocessenum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 Bir koleksiyonu çapraz yöntemleri sağlar `ICorPublishProcess` nesneleri.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata ayıklama coclass'ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Hata ayıklama genel statik işlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Hata ayıklama numaralandırmaları](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Hata ayıklama yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
