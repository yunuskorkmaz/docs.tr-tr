---
title: "Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
caps.latest.revision: "63"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e23de3ea6e9693c05aa81da056ac7763bced8e9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="diagnosing-errors-with-managed-debugging-assistants"></a>Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama
Yönetilen hata ayıklama yardımcıları (MDAs), çalışma zamanı durum bilgilerini sağlamak için ortak dil çalışma zamanı (CLR) ile birlikte çalışan yardımlarda hata ayıklar. Yardımcılar, aksi takdirde yakalayamayacağınız çalışma zamanı olayları hakkında bilgi iletileri oluşturur. Yönetilen ve yönetilmeyen kod arasında geçiş yaparken ortaya çıkan bulması zor uygulama hatalarını yalıtmak için MDA'leri kullanabilirsiniz. Windows kayıt defterine bir anahtar ekleyerek veya bir ortam değişkenini ayarlayarak bütün MDA'leri etkinleştirebilir ya da devre dışı bırakabilirsiniz. Uygulama yapılandırma ayarlarını kullanarak belirli MDA'leri etkinleştirebilirsiniz. Uygulamanın yapılandırma dosyasındaki bazı tek MDA'ler için ek yapılandırma ayarları ayarlayabilirsiniz. Çalışma zamanı yüklendiğinde bu yapılandırma dosyaları ayrıştırıldığı için yönetilen uygulama başlamadan önce MDA'i etkinleştirmeniz gerekir. Zaten başlatılmış uygulamalar için MDA'i etkinleştiremezsiniz.  
  
> [!NOTE]
>  Bir MDA etkinleştirildiğinde, kodunuz bir hata ayıklayıcı altında yürütülmüyor olduğunda bile etkindir. Bir hata ayıklayıcı olmadığında bir MDA olayı oluşturulursa, işlenmemiş özel bir durum olmasa bile olay iletisi, işlenmemiş özel durum iletişim kutusunda sunulur. İletişim kutusunu önlemek için kodunuz hata ayıklama ortamında çalışmıyorken MDA etkinleştirme ayarlarını kaldırın.  
  
> [!NOTE]
>  Kodunuz Visual Studio ile tümleşik geliştirme ortamında (IDE) çalışırken, belirli MDA olayları için görüntülenen özel durum iletişim kutusunu önleyebilirsiniz. Yapmak için **hata ayıklama** menüsünde tıklatın **özel durumları**. (Varsa **hata ayıklama** menü içermiyor bir **özel durumları** komutu, tıklatın **Özelleştir** üzerinde **Araçları** eklemek için menü.) İçinde **özel durumları** iletişim kutusunda, genişletin **yönetilen hata ayıklama Yardımcıları** listesine ve ardından temizlemek **sayıcı** tek tek mda'sı için onay kutusunu işaretleyin. Örneğin, özel durum iletişim kutusu için önlemek için bir [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) temizleyin **sayıcı** adının yanındaki onay kutusunu **yönetilen hata ayıklama Yardımcıları** listesi. Bu iletişim kutusunu aynı zamanda MDA özel iletişim kutularının görüntülenmesini etkinleştirmek için kullanabilirsiniz.  
  
 Aşağıdaki tablo .NET Framework ile birlikte gelen MDA'leri listeler.  
  
|||  
|-|-|  
|[asynchronousThreadAbort](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[bindingFailure](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|  
|[callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|  
|[dangerousThreadingAPI](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|  
|[dirtyCastAndCallOnInterface](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[disconnectedContext](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|  
|[dllMainReturnsFalse](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|  
|[failedQI](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[fatalExecutionEngineError](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|  
|[gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|  
|[illegalPrepareConstrainedRegion](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[InvalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|  
|[invalidCERCall](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|  
|[invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|  
|[invalidMemberDeclaration](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|  
|[invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|  
|[loaderLock](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[loadFromContext](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|  
|[marshalCleanupError](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[Hazırlama](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|  
|[memberInfoCacheCreation](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[moduloObjectHashcode](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|  
|[nonComVisibleBaseClass](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[notMarshalable](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|  
|[openGenericCERCall](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|  
|[pInvokeLog](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|  
|[raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[yeniden giriş](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|  
|[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|  
|[streamWriterBufferedDataLost](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[virtualCERCall](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|  
  
 Varsayılan olarak, .NET Framework yönetilen tüm hata ayıklayıcıları için bir MDA alt kümesini etkinleştirir. Visual Studio'da tıklayarak varsayılan görüntüleyebilirsiniz **özel durumları** üzerinde **hata ayıklama** menü ve genişletme **yönetilen hata ayıklama Yardımcıları** listesi.  
  
## <a name="enabling-and-disabling-mdas"></a>MDA'leri Etkinleştirme ve Devre Dışı Bırakma  
 Bir kayıt defteri anahtarını, bir ortam değişkenini ve uygulama yapılandırma ayarlarını kullanarak MDA'leri etkinleştirebilir ve devre dışı bırakabilirsiniz. Uygulama yapılandırma ayarlarını kullanmak için kayıt defteri anahtarını veya ortam değişkenini etkinleştirmeniz gerekir.  
  
 Visual Studio 2005 ve sonraki sürümlerinde, barındırma işlemi etkinleştirildiğinde varsayılan kümedeki MDA'leri devre dışı bırakamaz veya varsayılan kümede olmayan MDA'leri etkinleştiremezsiniz. Barındırma işlemi varsayılan olarak etkindir, bu nedenle açıkça devre dışı bırakılması gerekir.  
  
 Visual Studio'da barındırma işlemini devre dışı bırakmak için şunları yapın:  
  
1.  İçinde **Çözüm Gezgini**, bir proje seçin.  
  
2.  Üzerinde **proje** menüsünde tıklatın **özellikleri**.  
  
     **Proje Tasarımcısı** penceresi görüntülenir.  
  
3.  Tıklatın **hata ayıklama** sekmesi.  
  
4.  İçinde **etkinleştirmek hata ayıklayıcıları** bölümünde, Temizle **barındırma işlemi Visual Studio'nun** onay kutusu.  
  
 Ancak, barındırma işleminin devre dışı bırakılması performansı etkileyebilir. Bir MDA bildirimi alındığında Visual Studio'nun MDA iletişim kutusunu görüntülemesini engelleyerek MDA'leri devre dışı bırakma zorunluluğunu önleyebilirsiniz. Bunu yapmak için tıklatın **özel durumları** üzerinde **hata ayıklama** menüsünde genişletin **yönetilen hata ayıklama Yardımcıları** listesinde ve ardından seçin veya temizleyin **sayıcı**tek tek mda'sı için onay kutusunu işaretleyin.  
  
### <a name="enabling-and-disabling-mdas-by-using-a-registry-key"></a>Bir Kayıt Defteri Anahtarı Kullanarak MDA'leri Etkinleştirme ve Devre Dışı Bırakma  
 Mda'lar HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft ekleyerek etkinleştirebilirsiniz\\. Windows kayıt defterinde NETFramework\MDA alt (türü REG_SZ, 1 değeri). Aşağıdaki örnek MDAEnable.reg adlı bir metin dosyasına kopyalayın. Windows Kayıt Defteri Düzenleyicisi'ni (RegEdit.exe) açın ve **dosya** menüsünü seçin **alma**. Bu bilgisayar üzerinde Mda'lar etkinleştirmek için MDAEnable.reg dosyasını seçin. Alt dize değeri 1 (değil DWORD değerini 1) ayarını etkinleştirir MDA ayarlarından okuma *ApplicationName.suffix*. mda.config dosya. (Örneğin Not Defteri MDA yapılandırma dosyası notepad.exe.mda.config sayfadayken)  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 Ardından MDA anahtarı, bilgisayarın bir 64-bit işletim sisteminde 32 bit uygulama çalışıyorsa, aşağıdaki gibi ayarlanmalıdır:  
  
```  
      Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 Bkz: [etkinleştirme ve devre dışı bırakma Mda'lar kullanarak uygulamaya özgü yapılandırma ayarlarını tarafından](#appConfig) daha fazla bilgi için. Kayıt defteri ayarı, COMPLUS_MDA ortam değişkeni tarafından geçersiz kılınabilir. Bkz: [etkinleştirme ve devre dışı bırakma bir ortam değişkeni kullanarak Mda'lar](#envVariable) daha fazla bilgi için.  
  
 MDA'leri devre dışı bırakmak için Windows Kayıt Defteri Düzenleyicisi'ni kullanarak MDA alt anahtarını 0 (sıfır) olarak ayarlayın.  
  
 Bir hata ayıklayıcıya bağlı bir uygulamayı çalıştırdığınızda kayıt defteri anahtarı bile eklemeden bazı MDA'ler varsayılan olarak etkinleştirilir. Bu tür Yardımcıları örnekleri [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) ve [InvalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md). Bu yardımcıları, MDADisable.reg dosyasını bu bölümde daha önce açıklandığı şekilde çalıştırarak devre dışı bırakabilirsiniz.  
  
<a name="envVariable"></a>   
### <a name="enabling-and-disabling-mdas-by-using-an-environment-variable"></a>Bir Ortam Değişkeni Kullanarak MDA'leri Devre Etkinleştirme ve Devre Dışı Bırakma  
 MDA etkinleştirmesi aynı zamanda, kayıt defteri anahtarını geçersiz kılan COMPLUS_MDA ortam değişkeni tarafından da kontrol edilebilir. COMPLUS_MDA dizesi, MDA adlarının veya başka özel denetim dizelerinin büyük/küçük harf duyarlı, noktalı virgülle ayrılmış listesidir. Yönetilen veya yönetilmeyen hata ayıklayıcı altında başlamak varsayılan olarak bir MDA kümesini etkinleştirir. Bu, varsayılan olarak hata ayıklayıcılarda etkinleştirilen, noktalı virgülle ayrılmış MDA listesini ortam değişkeninin veya kayıt defteri anahtarının değerine açıkça ekleyerek yapılır. Özel denetim dizeleri şunlardır:  
  
-   `0` - Tüm MDA'leri devre dışı bırakır.  
  
-   `1`-MDA ayarlarından okur *ApplicationName*. mda.config.  
  
-   `managedDebugger` - Yönetilen bir yürütülebilir dosya hata ayıklayıcı altında başlatıldığında dolaylı olarak etkinleştirilmiş tüm MDA'leri açıkça etkinleştirir.  
  
-   `unmanagedDebugger` - Yönetilmeyen bir yürütülebilir dosya hata ayıklayıcı altında başlatıldığında dolaylı olarak etkinleştirilmiş tüm MDA'leri açıkça etkinleştirir.  
  
 Çakışan ayarlar varsa, en son ayarlar önceki ayarları geçersiz kılar:  
  
-   `COMPLUS_MDA=0`, dolaylı olarak bir hata ayıklayıcıda etkinleştirilmiş olanlar dahil olmak üzere tüm MDA'leri devre dışı bırakır.  
  
-   `COMPLUS_MDA=gcUnmanagedToManaged`, bir hata ayıklayıcıda dolaylı olarak etkinleştirilen MDA'lere ek olarak `gcUnmanagedToManaged` öğesini etkinleştirir.  
  
-   `COMPLUS_MDA=0;gcUnmanagedToManaged`, `gcUnmanagedToManaged` öğesini etkinleştirir, ancak aksi takdirde dolaylı olarak bir hata ayıklayıcıda etkinleştirilecek olan MDA'leri devre dışı bırakır.  
  
<a name="appConfig"></a>   
### <a name="enabling-and-disabling-mdas-by-using-application-specific-configuration-settings"></a>Uygulamaya Özgü Yapılandırma Ayarlarını Kullanarak MDA'leri Etkinleştirme ve Devre Dışı Bırakma  
 Uygulamaya ait MDA yapılandırma dosyası içinde bazı yardımcıları etkinleştirebilir, devre dışı bırakabilir ve ayrı ayrı yapılandırabilirsiniz. MDA'leri yapılandırmak üzere bir uygulama yapılandırma dosyasının kullanımını etkinleştirmek için MDA kayıt defteri anahtarının veya COMPLUS_MDA ortam değişkeni ayarlanması gerekir. Uygulama yapılandırma dosyası, genellikle uygulamanın yürütülebilir (.exe) dosyası ile aynı dizinde bulunur. Dosya adı şu biçimi alır *ApplicationName*. mda.config; Örneğin, notepad.exe.mda.config. Uygulama yapılandırma dosyasında etkinleştirilen yardımcılar, o yardımcının davranışını denetlemek için özel olarak tasarlanan özniteliklere veya öğelere sahip olabilir. Aşağıdaki örnek, etkinleştirme ve yapılandırma gösterilmektedir [hazırlama](../../../docs/framework/debug-trace-profile/marshaling-mda.md).  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="*"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="*"/>  
      </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
 `Marshaling` MDA, uygulamadaki her yönetilenden yönetilmeyene geçiş için bir yönetilmeyen türe sıraya koyulan yönetilen tür hakkında bilgiler verir. `Marshaling` MDA aynı zamanda `<methodFilter>` ve `<fieldFilter>` alt öğelerinde sağlanan yöntem ve yapı alanlarının adlarını filtreler.  
  
 Aşağıdaki örnekte, varsayılan ayarlarını kullanarak birden çok MDA'in nasıl etkinleştirileceği gösterilir.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion />  
    <invalidCERCall />  
    <openGenericCERCall />  
    <virtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
> [!IMPORTANT]
>  Bir yapılandırma dosyasında birden fazla yardımcı belirttiğinizde, bunları alfabetik olarak listelemeniz gerekir. Örneğin, `virtualCERCall` ve `invalidCERCall` MDA'lerinin her ikisini de etkinleştirmek istiyorsanız `<invalidCERCall />` girdisinden önce `<virtualCERCall />` girdisini eklemeniz gerekir. Girdiler alfabetik sırada değilse, işlenmemiş bir geçersiz yapılandırma dosyası özel durum iletisi görüntülenir.  
  
### <a name="mda-output"></a>MDA Çıktısı  
 MDA çıktısı, `pInvokeStackImbalance` MDA öğesinin çıktısını gösteren aşağıdaki örneğe benzerdir.  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama, izleme ve profil oluşturma](../../../docs/framework/debug-trace-profile/index.md)
