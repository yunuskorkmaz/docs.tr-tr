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
ms.openlocfilehash: 6cb2a240a2e7e82b7015eb7a6d99c2117fa63045
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052894"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>Yönetilen hata ayıklama yardımcıları ile hataları tanılama

Yönetilen hata ayıklama yardımcıları (MDAs), çalışma zamanı durum bilgilerini sağlamak için ortak dil çalışma zamanı (CLR) ile birlikte çalışan yardımlarda hata ayıklar. Yardımcılar, aksi takdirde yakalayamayacağınız çalışma zamanı olayları hakkında bilgi iletileri oluşturur. Yönetilen ve yönetilmeyen kod arasında geçiş yaparken ortaya çıkan bulması zor uygulama hatalarını yalıtmak için MDA'leri kullanabilirsiniz.

Windows kayıt defterine bir anahtar ekleyerek veya bir ortam değişkenini ayarlayarak tüm Mdaları [etkinleştirebilir veya devre dışı](#enable-and-disable-mdas) bırakabilirsiniz. Uygulama yapılandırma ayarlarını kullanarak belirli MDA'leri etkinleştirebilirsiniz. Uygulamanın yapılandırma dosyasındaki bazı tek MDA'ler için ek yapılandırma ayarları ayarlayabilirsiniz. Çalışma zamanı yüklendiğinde bu yapılandırma dosyaları ayrıştırıldığı için yönetilen uygulama başlamadan önce MDA'i etkinleştirmeniz gerekir. Zaten başlatılmış uygulamalar için MDA'i etkinleştiremezsiniz.

Aşağıdaki tabloda .NET Framework ile birlikte gelen Mdalar listelenmektedir:

|||
|-|-|
|[asynchronousThreadAbort](asynchronousthreadabort-mda.md)|[bindingFailure](bindingfailure-mda.md)|
|[callbackOnCollectedDelegate](callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](contextswitchdeadlock-mda.md)|
|[dangerousThreadingAPI](dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](datetimeinvalidlocalformat-mda.md)|
|[dirtyCastAndCallOnInterface](dirtycastandcalloninterface-mda.md)|[disconnectedContext](disconnectedcontext-mda.md)|
|[dllMainReturnsFalse](dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](exceptionswallowedoncallfromcom-mda.md)|
|[failedQI](failedqi-mda.md)|[fatalExecutionEngineError](fatalexecutionengineerror-mda.md)|
|[gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)|
|[illegalPrepareConstrainedRegion](illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](invalidapartmentstatechange-mda.md)|
|[invalidCERCall](invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](invalidfunctionpointerindelegate-mda.md)|
|[invalidGCHandleCookie](invalidgchandlecookie-mda.md)|[invalidIUnknown](invalidiunknown-mda.md)|
|[invalidMemberDeclaration](invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](invalidoverlappedtopinvoke-mda.md)|
|[invalidVariant](invalidvariant-mda.md)|[jitCompilationStart](jitcompilationstart-mda.md)|
|[loaderLock](loaderlock-mda.md)|[loadFromContext](loadfromcontext-mda.md)|
|[marshalCleanupError](marshalcleanuperror-mda.md)|[marshaling](marshaling-mda.md)|
|[memberInfoCacheCreation](memberinfocachecreation-mda.md)|[moduloObjectHashcode](moduloobjecthashcode-mda.md)|
|[nonComVisibleBaseClass](noncomvisiblebaseclass-mda.md)|[notMarshalable](notmarshalable-mda.md)|
|[openGenericCERCall](opengenericcercall-mda.md)|[overlappedFreeError](overlappedfreeerror-mda.md)|
|[pInvokeLog](pinvokelog-mda.md)|[pInvokeStackImbalance](pinvokestackimbalance-mda.md)|
|[raceOnRCWCleanup](raceonrcwcleanup-mda.md)|[reentrancy](reentrancy-mda.md)|
|[releaseHandleFailed](releasehandlefailed-mda.md)|[reportAvOnComRelease](reportavoncomrelease-mda.md)|
|[streamWriterBufferedDataLost](streamwriterbuffereddatalost-mda.md)|[virtualCERCall](virtualcercall-mda.md)|

Varsayılan olarak, .NET Framework yönetilen tüm hata ayıklayıcıları için bir MDA alt kümesini etkinleştirir. Visual Studio 'da varsayılan kümeyi **Hata Ayıkla** menüsündeki **Windows** > **özel durum ayarları** ' nı seçerek ve ardından **yönetilen hata ayıklama yardımcıları** listesini genişleterek görüntüleyebilirsiniz.

![Visual Studio 'da özel durum ayarları penceresi](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>Mdaları etkinleştirme ve devre dışı bırakma

Bir kayıt defteri anahtarını, bir ortam değişkenini ve uygulama yapılandırma ayarlarını kullanarak MDA'leri etkinleştirebilir ve devre dışı bırakabilirsiniz. Uygulama yapılandırma ayarlarını kullanmak için kayıt defteri anahtarını veya ortam değişkenini etkinleştirmeniz gerekir.

> [!TIP]
> MDAs 'yi devre dışı bırakmak yerine, bir MDA bildirimi alındığında Visual Studio 'Nun MDA iletişim kutusunu görüntülemesini engelleyebilirsiniz. Bunu yapmak için, **hata ayıklama** menüsünde **Windows** > **özel durum ayarları** ' nı seçin, **yönetilen hata ayıklama yardımcıları** listesini genişletin ve sonra tek bir mda için **oluşturulduğunda kes** onay kutusunu seçin veya temizleyin.

### <a name="registry-key"></a>Kayıt Defteri Anahtarı

MDAs 'yi etkinleştirmek için **HKEY_LOCAL_MACHINE\Software\Microsoft\\ekleyin. Windows kayıt defteri 'nde NETFramework\MDA** alt anahtarı (REG_SZ, değer 1 yazın). Aşağıdaki örneği *Mdadenable. reg*adlı bir metin dosyasına kopyalayın. Windows kayıt defteri Düzenleyicisi 'Ni (RegEdit. exe) açın ve **Dosya** menüsünden **içeri aktar**' ı seçin. Bu bilgisayarda MDAs 'yi etkinleştirmek için *MDAEnable. reg* dosyasını seçin. Alt anahtarı **1** ' in dize DEĞERINE (DWORD değeri **1**değil) ayarlamak, *ApplicationName. suffix*. mda. config dosyasından MDA ayarlarının okunmasına olanak sağlar. Örneğin, Notepad için MDA yapılandırma dosyası Notepad. exe. mda. config olarak adlandırılır.

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

Bilgisayar 64 bit işletim sisteminde 32 bitlik bir uygulama çalıştırıyorsa, MDA anahtarı aşağıdaki gibi ayarlanmalıdır:

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

Daha fazla bilgi için [uygulamaya özgü yapılandırma ayarlarına](#application-specific-configuration-settings) bakın. Kayıt defteri ayarı, COMPLUS_MDA ortam değişkeni tarafından geçersiz kılınabilir. Daha fazla bilgi için bkz. [ortam değişkeni](#environment-variable) .

MDAs 'yi devre dışı bırakmak için, Windows kayıt defteri düzenleyicisini kullanarak MDA alt anahtarını **0** (sıfır) olarak ayarlayın.

Bir hata ayıklayıcıya bağlı bir uygulamayı çalıştırdığınızda kayıt defteri anahtarı bile eklemeden bazı MDA'ler varsayılan olarak etkinleştirilir. Bu bölümün önceki kısımlarında açıklandığı gibi *Mdaddisable. reg* dosyasını çalıştırarak bu yardımcıları devre dışı bırakabilirsiniz.

### <a name="environment-variable"></a>Ortam değişkeni

MDA etkinleştirmesi aynı zamanda, kayıt defteri anahtarını geçersiz kılan COMPLUS_MDA ortam değişkeni tarafından da kontrol edilebilir. COMPLUS_MDA dizesi, MDA adlarının veya başka özel denetim dizelerinin büyük/küçük harf duyarlı, noktalı virgülle ayrılmış listesidir. Yönetilen veya yönetilmeyen hata ayıklayıcı altında başlamak varsayılan olarak bir MDA kümesini etkinleştirir. Bu, varsayılan olarak hata ayıklayıcılarda etkinleştirilen, noktalı virgülle ayrılmış MDA listesini ortam değişkeninin veya kayıt defteri anahtarının değerine açıkça ekleyerek yapılır. Özel denetim dizeleri şunlardır:

- `0` - Tüm MDA'leri devre dışı bırakır.

- `1`- *ApplicationName*. mda. CONFIG dosyasından MDA ayarlarını okur.

- `managedDebugger` - Yönetilen bir yürütülebilir dosya hata ayıklayıcı altında başlatıldığında dolaylı olarak etkinleştirilmiş tüm MDA'leri açıkça etkinleştirir.

- `unmanagedDebugger` - Yönetilmeyen bir yürütülebilir dosya hata ayıklayıcı altında başlatıldığında dolaylı olarak etkinleştirilmiş tüm MDA'leri açıkça etkinleştirir.

Çakışan ayarlar varsa, en son ayarlar önceki ayarları geçersiz kılar:

- `COMPLUS_MDA=0`, dolaylı olarak bir hata ayıklayıcıda etkinleştirilmiş olanlar dahil olmak üzere tüm MDA'leri devre dışı bırakır.

- `COMPLUS_MDA=gcUnmanagedToManaged`, bir hata ayıklayıcıda dolaylı olarak etkinleştirilen MDA'lere ek olarak `gcUnmanagedToManaged` öğesini etkinleştirir.

- `COMPLUS_MDA=0;gcUnmanagedToManaged`, `gcUnmanagedToManaged` öğesini etkinleştirir, ancak aksi takdirde dolaylı olarak bir hata ayıklayıcıda etkinleştirilecek olan MDA'leri devre dışı bırakır.

### <a name="application-specific-configuration-settings"></a>Uygulamaya özgü yapılandırma ayarları

Uygulamaya ait MDA yapılandırma dosyası içinde bazı yardımcıları etkinleştirebilir, devre dışı bırakabilir ve ayrı ayrı yapılandırabilirsiniz. MDA'leri yapılandırmak üzere bir uygulama yapılandırma dosyasının kullanımını etkinleştirmek için MDA kayıt defteri anahtarının veya COMPLUS_MDA ortam değişkeni ayarlanması gerekir. Uygulama yapılandırma dosyası, genellikle uygulamanın yürütülebilir (.exe) dosyası ile aynı dizinde bulunur. Dosya adı, *ApplicationName*. mda. config biçimini alır; Örneğin, Notepad. exe. mda. config. Uygulama yapılandırma dosyasında etkinleştirilen yardımcılar, o yardımcının davranışını denetlemek için özel olarak tasarlanan özniteliklere veya öğelere sahip olabilir.

Aşağıdaki örnek, [hazırlamayı](marshaling-mda.md)nasıl etkinleştireceğinizi ve yapılandıracağınızı göstermektedir:

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

`Marshaling` MDA, uygulamadaki her yönetilenden yönetilmeyene geçiş için bir yönetilmeyen türe sıraya koyulan yönetilen tür hakkında bilgiler verir. MDA, sırasıyla **methodFilter** ve **FieldFilter** alt öğelerinde sağlanan yöntem ve yapı alanlarının adlarını da filtreleyebilirler. `Marshaling`

Aşağıdaki örnek, varsayılan ayarlarını kullanarak birden çok Mdayı nasıl etkinleştireceğinizi göstermektedir:

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

## <a name="mda-exceptions"></a>MDA özel durumlar

Bir MDA etkinleştirildiğinde, kodunuz bir hata ayıklayıcı altında yürütülmediğinde bile etkin olur. Bir hata ayıklayıcı olmadığında bir MDA olayı oluşturulursa, işlenmemiş özel bir durum olmasa bile olay iletisi, işlenmemiş özel durum iletişim kutusunda sunulur. İletişim kutusunu önlemek için kodunuz hata ayıklama ortamında çalışmıyorken MDA etkinleştirme ayarlarını kaldırın.

Kodunuz Visual Studio tümleşik geliştirme ortamında (IDE) yürütüldüğünde, belirli MDA olayları için görüntülenen özel durum iletişim kutusunu önleyebilirsiniz. Bunu yapmak için, **Hata Ayıkla** menüsünde **Windows** > **özel durum ayarları**' nı seçin. **Özel durum ayarları** penceresinde, **yönetilen hata ayıklama yardımcıları** listesini genişletin ve sonra tek bir mda için **oluşturulan** onay kutusunu temizleyin. Bu iletişim kutusunu, MDA özel durum iletişim kutularının görüntülenmesini *sağlamak* için de kullanabilirsiniz.

## <a name="mda-output"></a>MDA Çıktısı

Mda çıktısı, `PInvokeStackImbalance` mda ' dan çıktıyı gösteren aşağıdaki örneğe benzer.

**PInvoke işlevi ' Mdadtest! ' çağrısı Mdadtest. Program:: StdCall ', yığına dengesiz. Bu, yönetilen PInvoke imzasının yönetilmeyen hedef imzasıyla eşleşmemesi nedeniyle olasıdır. PInvoke imzasının çağırma kuralı ve parametrelerinin hedef yönetilmeyen imzayla eşleşip eşleştiğinden emin olun.**

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama, İzleme ve Profil Oluşturma](index.md)
