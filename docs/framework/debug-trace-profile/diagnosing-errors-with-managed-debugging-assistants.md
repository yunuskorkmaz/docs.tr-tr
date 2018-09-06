---
title: Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama
ms.date: 08/14/2018
f1_keywords:
- EHMDA
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873175"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>Yönetilen hata ayıklama Yardımcıları ile hataları tanılama

Yönetilen hata ayıklama yardımcıları (MDAs), çalışma zamanı durum bilgilerini sağlamak için ortak dil çalışma zamanı (CLR) ile birlikte çalışan yardımlarda hata ayıklar. Yardımcılar, aksi takdirde yakalayamayacağınız çalışma zamanı olayları hakkında bilgi iletileri oluşturur. Yönetilen ve yönetilmeyen kod arasında geçiş yaparken ortaya çıkan bulması zor uygulama hatalarını yalıtmak için MDA'leri kullanabilirsiniz.

Yapabilecekleriniz [etkinleştirmek veya devre dışı](#enable-and-disable-mdas) tüm Mda'leri Windows kayıt defterine bir anahtar ekleyerek veya bir ortam değişkenini ayarlayarak. Uygulama yapılandırma ayarlarını kullanarak belirli MDA'leri etkinleştirebilirsiniz. Uygulamanın yapılandırma dosyasındaki bazı tek MDA'ler için ek yapılandırma ayarları ayarlayabilirsiniz. Çalışma zamanı yüklendiğinde bu yapılandırma dosyaları ayrıştırıldığı için yönetilen uygulama başlamadan önce MDA'i etkinleştirmeniz gerekir. Zaten başlatılmış uygulamalar için MDA'i etkinleştiremezsiniz.

Aşağıdaki tablo, .NET Framework ile birlikte gelen Mda'leri listeler:

|||
|-|-|
|[asynchronousThreadAbort](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[bindingFailure](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|
|[callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|
|[dangerousThreadingAPI](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|
|[dirtyCastAndCallOnInterface](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[disconnectedContext](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|
|[dllMainReturnsFalse](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|
|[failedQI](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[fatalExecutionEngineError](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|
|[gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|
|[illegalPrepareConstrainedRegion](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|
|[invalidCERCall](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|
|[invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|
|[invalidMemberDeclaration](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|
|[invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|
|[loaderLock](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[loadFromContext](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|
|[marshalCleanupError](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|
|[memberInfoCacheCreation](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[moduloObjectHashcode](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|
|[nonComVisibleBaseClass](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[notMarshalable](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|
|[openGenericCERCall](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|
|[pInvokeLog](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|
|[raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[reentrancy](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|
|[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|
|[streamWriterBufferedDataLost](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[virtualCERCall](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|

Varsayılan olarak, .NET Framework yönetilen tüm hata ayıklayıcıları için bir MDA alt kümesini etkinleştirir. Visual Studio'da seçerek varsayılan görüntüleyebileceğiniz **Windows** > **özel durum ayarları** üzerinde **hata ayıklama** menüsüne ve ardından genişletme**Yönetilen hata ayıklama Yardımcıları** listesi.

![Visual Studio'da özel durum Ayarları penceresi](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>Etkinleştirme ve Mda'leri devre dışı bırak

Bir kayıt defteri anahtarını, bir ortam değişkenini ve uygulama yapılandırma ayarlarını kullanarak MDA'leri etkinleştirebilir ve devre dışı bırakabilirsiniz. Uygulama yapılandırma ayarlarını kullanmak için kayıt defteri anahtarını veya ortam değişkenini etkinleştirmeniz gerekir.

> [!TIP]
> Mda'leri devre dışı bırakmak yerine Visual Studio bir MDA bildirimi alındığında MDA iletişim kutusunu görüntülemesini engelleyebilirsiniz. Bunu yapmak için seçin **Windows** > **özel durum ayarları** üzerinde **hata ayıklama** menüsünü genişletin **yönetilen hata ayıklama Yardımcıları**listesini ve ardından seçin veya temizleyin **Break When Thrown** tek mda'e onay kutusu.

### <a name="registry-key"></a>Kayıt Defteri Anahtarı

Mda'leri etkinleştirmek için eklemeniz **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\MDA** Windows kayıt defteri alt anahtarında (tür REG_SZ, değer 1). Aşağıdaki örnekte adlı bir metin dosyasına kopyalama *MDAEnable.reg*. Windows Kayıt Defteri Düzenleyicisi'ni (RegEdit.exe) açın ve **dosya** menüsünde **alma**. Seçin *MDAEnable.reg* o bilgisayardaki Mda'leri etkinleştirmek için dosya. Alt dize değeri olarak ayarlama **1** (DWORD değerini değil **1**) MDA ayarlarının okunmasını etkinleştirir *ApplicationName.suffix*. mda.config dosyasından. Örneğin, Not Defteri ait MDA yapılandırma dosyası, notepad.exe.mda.config sayfadayken.

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

Ardından MDA anahtarı, bilgisayar, 64-bit işletim sisteminde 32 bit uygulama çalışıyorsa, aşağıdaki gibi ayarlanmalıdır:

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

Bkz: [uygulamaya özgü yapılandırma ayarlarını](#application-specific-configuration-settings) daha fazla bilgi için. Kayıt defteri ayarı, COMPLUS_MDA ortam değişkeni tarafından geçersiz kılınabilir. Bkz: [ortam değişkeni](#environment-variable) daha fazla bilgi için.

Mda'leri devre dışı bırakmak için MDA alt anahtarını ayarlamak **0** (Windows Kayıt Defteri Düzenleyicisi'ni kullanarak sıfır).

Bir hata ayıklayıcıya bağlı bir uygulamayı çalıştırdığınızda kayıt defteri anahtarı bile eklemeden bazı MDA'ler varsayılan olarak etkinleştirilir. Çalıştırarak bu Yardımcıları devre dışı bırakabilirsiniz *MDADisable.reg* dosya bu bölümde daha önce açıklandığı gibi.

### <a name="environment-variable"></a>Ortam değişkeni

MDA etkinleştirmesi aynı zamanda, kayıt defteri anahtarını geçersiz kılan COMPLUS_MDA ortam değişkeni tarafından da kontrol edilebilir. COMPLUS_MDA dizesi, MDA adlarının veya başka özel denetim dizelerinin büyük/küçük harf duyarlı, noktalı virgülle ayrılmış listesidir. Yönetilen veya yönetilmeyen hata ayıklayıcı altında başlamak varsayılan olarak bir MDA kümesini etkinleştirir. Bu, varsayılan olarak hata ayıklayıcılarda etkinleştirilen, noktalı virgülle ayrılmış MDA listesini ortam değişkeninin veya kayıt defteri anahtarının değerine açıkça ekleyerek yapılır. Özel denetim dizeleri şunlardır:

- `0` - Tüm MDA'leri devre dışı bırakır.

- `1` -MDA ayarlarını okur *ApplicationName*. mda.config.

- `managedDebugger` - Yönetilen bir yürütülebilir dosya hata ayıklayıcı altında başlatıldığında dolaylı olarak etkinleştirilmiş tüm MDA'leri açıkça etkinleştirir.

- `unmanagedDebugger` - Yönetilmeyen bir yürütülebilir dosya hata ayıklayıcı altında başlatıldığında dolaylı olarak etkinleştirilmiş tüm MDA'leri açıkça etkinleştirir.

Çakışan ayarlar varsa, en son ayarlar önceki ayarları geçersiz kılar:

- `COMPLUS_MDA=0`, dolaylı olarak bir hata ayıklayıcıda etkinleştirilmiş olanlar dahil olmak üzere tüm MDA'leri devre dışı bırakır.

- `COMPLUS_MDA=gcUnmanagedToManaged`, bir hata ayıklayıcıda dolaylı olarak etkinleştirilen MDA'lere ek olarak `gcUnmanagedToManaged` öğesini etkinleştirir.

- `COMPLUS_MDA=0;gcUnmanagedToManaged`, `gcUnmanagedToManaged` öğesini etkinleştirir, ancak aksi takdirde dolaylı olarak bir hata ayıklayıcıda etkinleştirilecek olan MDA'leri devre dışı bırakır.

### <a name="application-specific-configuration-settings"></a>Uygulamaya özgü yapılandırma ayarları

Uygulamaya ait MDA yapılandırma dosyası içinde bazı yardımcıları etkinleştirebilir, devre dışı bırakabilir ve ayrı ayrı yapılandırabilirsiniz. MDA'leri yapılandırmak üzere bir uygulama yapılandırma dosyasının kullanımını etkinleştirmek için MDA kayıt defteri anahtarının veya COMPLUS_MDA ortam değişkeni ayarlanması gerekir. Uygulama yapılandırma dosyası, genellikle uygulamanın yürütülebilir (.exe) dosyası ile aynı dizinde bulunur. Dosya adı biçimi alır *ApplicationName*. mda.config biçimini alır; Örneğin, notepad.exe.mda.config. Uygulama yapılandırma dosyasında etkinleştirilen yardımcılar, o yardımcının davranışını denetlemek için özel olarak tasarlanan özniteliklere veya öğelere sahip olabilir.

Aşağıdaki örnek, etkinleştirme ve yapılandırma gösterilmektedir [hazırlama](../../../docs/framework/debug-trace-profile/marshaling-mda.md):

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

`Marshaling` MDA, uygulamadaki her yönetilenden yönetilmeyene geçiş için bir yönetilmeyen türe sıraya koyulan yönetilen tür hakkında bilgiler verir. `Marshaling` MDA aynı zamanda yöntem adlarını filtrelemek ve yapı alanlarının sağlanan **methodFilter** ve **alan filtresi** alt öğeleri, sırasıyla.

Aşağıdaki örnek, varsayılan ayarlarını kullanarak birden çok Mda'in etkinleştirmek gösterilmektedir:

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
> Bir yapılandırma dosyasında birden fazla yardımcı belirttiğinizde, bunları alfabetik olarak listelemeniz gerekir. Örneğin, `virtualCERCall` ve `invalidCERCall` MDA'lerinin her ikisini de etkinleştirmek istiyorsanız `<invalidCERCall />` girdisinden önce `<virtualCERCall />` girdisini eklemeniz gerekir. Girdiler alfabetik sırada değilse, işlenmemiş bir geçersiz yapılandırma dosyası özel durum iletisi görüntülenir.

## <a name="mda-exceptions"></a>MDA özel durumları

Bir MDA etkinleştirildiğinde, hatta zaman kodunuzu hata ayıklayıcı altında yürütülmüyor olduğunda etkin değil. Bir hata ayıklayıcı olmadığında bir MDA olayı oluşturulursa, işlenmemiş özel bir durum olmasa bile olay iletisi, işlenmemiş özel durum iletişim kutusunda sunulur. İletişim kutusunu önlemek için kodunuz hata ayıklama ortamında çalışmıyorken MDA etkinleştirme ayarlarını kaldırın.

Kodunuzu Visual Studio tümleşik geliştirme ortamında (IDE) yürütüldüğünde, belirli MDA olayları için görüntülenen özel durum iletişim kutusunu önleyebilirsiniz. Bunu yapmak için **hata ayıklama** menüsünde seçin **Windows** > **özel durum ayarları**. İçinde **özel durum ayarları** penceresini genişletin **yönetilen hata ayıklama Yardımcıları** listeleyin ve ardından temizleyin **Break When Thrown** tek mda'e onay kutusu. Bu iletişim kutusu için de kullanabilirsiniz *etkinleştirme* MDA özel iletişim kutularının görüntülenmesini.

## <a name="mda-output"></a>MDA Çıktısı

MDA çıktısı çıktısını gösteren aşağıdaki örneğe benzer `PInvokeStackImbalance` MDA:

**PInvoke işlevi çağrısı ' MDATest! MDATest.Program::StdCall' yığın dengesiz. Yönetilen PInvoke imza yönetilmeyen hedef imza eşleşmediği için büyük olasılıkla budur. Çağırma kuralı ve parametreleri PInvoke imza hedef yönetilmeyen imza eşleştiğinden emin olun.**

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama, İzleme ve Profil Oluşturma](../../../docs/framework/debug-trace-profile/index.md)
