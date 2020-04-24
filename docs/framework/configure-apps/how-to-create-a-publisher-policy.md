---
title: 'Nasıl yapılır: Yayımcı İlkesi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646052"
---
# <a name="how-to-create-a-publisher-policy"></a>Nasıl yapılır: Yayımcı İlkesi Oluşturma

Derleme satıcıları, uygulamaların yükseltilmiş derlemeye bir yayımcı ilke dosyası ekleyerek derlemenin daha yeni bir sürümünü kullanması gerektiğini belirtebilir. Yayımcı ilkesi dosyası, derleme yeniden yönlendirme ve kod tabanı ayarlarını belirtir ve uygulama yapılandırma dosyasıyla aynı biçimi kullanır. Yayımcı ilkesi dosyası bir derlemeiçine derlenir ve genel derleme önbelleğine yerleştirilir.

Yayımcı ilkesi oluşturmanın üç adımı vardır:

1. Yayımcı ilkesi dosyası oluşturun.

2. Yayımcı ilkesi derlemesi oluşturun.

3. Yayımcı ilkesi derlemesini genel derleme önbelleğine ekleyin.

Yayımcı ilkesi şeması [Derleme Sürümleri yönlendirme](redirect-assembly-versions.md)açıklanmıştır. Aşağıdaki örnek, bir sürümünü diğerine yönlendiren bir `myAssembly` yayımcı ilkesi dosyasını gösterir.

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

Kod tabanını nasıl belirtin, [bkz.](specify-assembly-location.md)

## <a name="creating-the-publisher-policy-assembly"></a>Yayımcı İlke Derlemesini Oluşturma

Yayımcı ilke derlemesini oluşturmak için [Derleme Bağlantı Cısı'nı (Al.exe)](../tools/al-exe-assembly-linker.md) kullanın.

#### <a name="to-create-a-publisher-policy-assembly"></a>Yayımcı ilkesi derlemesi oluşturmak için

Komut istemine aşağıdaki komutu yazın:

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

Şu komutta:

- Bağımsız `publisherPolicyFile` değişken, yayımcı ilkesi dosyasının adıdır.

- Bağımsız `publisherPolicyAssemblyFile` değişken, bu komuttan kaynaklanan yayımcı ilke derlemesinin adıdır. Derleme dosya adı biçimi izlemelidir:

  'policy.majorNumber.minorNumber.mainAssemblyName.dll'

- Bağımsız `keyPairFile` değişken, anahtar çiftini içeren dosyanın adıdır. Derleme ve yayımcı ilke derlemesini aynı anahtar çiftiyle imzalamanız gerekir.

- Bağımsız `processorArchitecture` değişken, işlemciye özgü bir derleme tarafından hedeflenen platformu tanımlar.

  > [!NOTE]
  > .NET Framework 2.0 ile başlayan belirli bir işlemci mimarisini hedefleme olanağı mevcuttur.

.NET Framework 2.0 ile başlayan belirli bir işlemci mimarisini hedefleme olanağı mevcuttur. Aşağıdaki komut, `policy.1.0.myAssembly` `pub.config` `sgKey.snk` dosyadaki anahtar çiftini kullanarak derlemeye güçlü bir ad atayan ve derlemenin x86 işlemci mimarisini hedefaldığını belirten yayımcı ilkesi dosyası ndan çağrılan bir yayımcı ilkesi derlemesi oluşturur.

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

Yayımcı ilke derlemesi, uygulandığı derlemenin işlemci mimarisiyle eşleşmelidir. Bu nedenle, derlemenizin <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> <xref:System.Reflection.ProcessorArchitecture.MSIL>bir değeri varsa, bu derleme için `/platform:anycpu`yayımcı ilke derlemesi . İşlemciye özgü her derleme için ayrı bir yayımcı ilkesi derlemesi sağlamanız gerekir.

Bu kuralın bir sonucu, bir derleme için işlemci mimarisini değiştirmek için, doğru işlemci mimarisi ile yeni bir yayımcı ilke derlemesi sağlamak için, sürüm numarasının büyük veya küçük bileşenini değiştirmeniz gerekir. Eski yayımcı ilke derlemesi, derlemeniz farklı bir işlemci mimarisine sahip olduktan sonra derlemenize hizmet veremez.

Başka bir sonuç, sürüm 2.0 bağlantı cısının .NET Framework'ün önceki sürümleri kullanılarak derlenen bir derleme için yayımcı ilkesi derlemesi oluşturmak için kullanılamamasıdır, çünkü her zaman işlemci mimarisini belirtir.

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı İlke Derlemesinin Küresel Meclis Önbelleğine Eklenmesi

Yayımcı ilke derlemesini genel derleme önbelleğine eklemek için [Genel Derleme Önbellek aracını (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) kullanın.

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı ilkesi derlemesini genel derleme önbelleğine eklemek için

Komut istemine aşağıdaki komutu yazın:

```console
gacutil /i publisherPolicyAssemblyFile
```

Aşağıdaki komut, `policy.1.0.myAssembly.dll` genel derleme önbelleğine ekler.

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> `/link` Bağımsız değişkende belirtilen özgün yayımcı ilkesi ilkesi dosyası derlemeyle aynı dizinde bulunmadığı sürece yayımcı ilkesi derlemesi genel derleme önbelleğine eklenemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemelerle Programlama](../../standard/assembly/index.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma](index.md)
- [Çalışma Zamanı Ayarları Şeması](./file-schema/runtime/index.md)
- [Yapılandırma Dosya Şema](./file-schema/index.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](redirect-assembly-versions.md)
