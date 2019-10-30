---
title: 'Nasıl yapılır: Yayımcı İlkesi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 346671d4febd5f3999f1f4fbf2fe4b7e475ae5fa
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040186"
---
# <a name="how-to-create-a-publisher-policy"></a>Nasıl yapılır: Yayımcı İlkesi Oluşturma

Derlemelerin satıcıları, yükseltilen derlemeye bir yayımcı ilke dosyası ekleyerek uygulamaların bir derlemenin daha yeni bir sürümünü kullanması gerektiğini belirtebilir. Yayımcı ilke dosyası, derleme yeniden yönlendirme ve kod tabanı ayarlarını belirtir ve bir uygulama yapılandırma dosyası ile aynı biçimi kullanır. Yayımcı ilke dosyası bir derlemede derlenir ve genel derleme önbelleğine yerleştirilir.

Yayımcı ilkesi oluşturma ile ilgili üç adım vardır:

1. Bir yayımcı ilke dosyası oluşturun.

2. Yayımcı ilkesi derlemesi oluşturun.

3. Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleyin.

Yayımcı ilkesi şeması, [derleme sürümlerini yeniden yönlendirme](redirect-assembly-versions.md)bölümünde açıklanmıştır. Aşağıdaki örnek, `myAssembly` bir sürümünü diğerine yönlendiren bir yayımcı ilkesi dosyası gösterir.

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

Bir kod tabanının nasıl belirtileceği hakkında bilgi edinmek için bkz. [derlemenin konumunu belirtme](specify-assembly-location.md).

## <a name="creating-the-publisher-policy-assembly"></a>Yayımcı Ilkesi derlemesi oluşturma

Yayımcı ilke derlemesini oluşturmak için [derleme Bağlayıcısı (al. exe)](../tools/al-exe-assembly-linker.md) kullanın.

#### <a name="to-create-a-publisher-policy-assembly"></a>Yayımcı ilkesi derlemesi oluşturmak için

Komut istemine aşağıdaki komutu yazın:

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

Bu komutta:

- `publisherPolicyFile` bağımsız değişkeni yayımcı ilkesi dosyasının adıdır.

- `publisherPolicyAssemblyFile` bağımsız değişkeni, bu komutun sonucu olan yayımcı ilkesi derlemesinin adıdır. Derleme dosyası adı şu biçimde olmalıdır:

  ' Policy. majorNumber. minorNumber. mainAssemblyName. dll '

- `keyPairFile` bağımsız değişkeni, anahtar çiftini içeren dosyanın adıdır. Derleme ve Yayımcı ilke derlemesini aynı anahtar çiftiyle imzalamanız gerekir.

- `processorArchitecture` bağımsız değişkeni, işlemciye özgü bir derleme tarafından hedeflenen platformu tanımlar.

  > [!NOTE]
  > Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework 2,0 ' den başlayarak kullanılabilir.

Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework 2,0 ' den başlayarak kullanılabilir. Aşağıdaki komut `pub.config`adlı bir yayımcı ilke dosyasından `policy.1.0.myAssembly` adlı bir yayımcı ilke derlemesi oluşturur, `sgKey.snk` dosyasında anahtar çiftini kullanarak derlemeye tanımlayıcı bir ad atar ve derlemenin x86 işlemcisini hedeflediğini belirtir mimarisini.

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

Yayımcı ilke derlemesinin, uygulandığı derlemenin işlemci mimarisiyle eşleşmesi gerekir. Bu nedenle, derlemenizin <xref:System.Reflection.ProcessorArchitecture.MSIL>bir <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> değeri varsa, bu derleme için yayımcı ilke derlemesinin `/platform:anycpu`ile oluşturulması gerekir. İşlemciye özgü her derleme için ayrı bir yayımcı ilke derlemesi sağlamalısınız.

Bu kuralın bir sonucu, bir derlemenin işlemci mimarisini değiştirmek için, sürüm numarasının büyük veya küçük bileşenini değiştirmeniz, böylece doğru işlemci mimarisine sahip yeni bir yayımcı ilke derlemesi sağlayabilmeniz gerekir. Derlemelerinizin farklı bir işlemci mimarisi varsa, eski yayımcı ilkesi derlemesi derlemenizi kullanamaz.

Bunun nedeni, sürüm 2,0 bağlayıcının, .NET Framework önceki sürümleri kullanılarak derlenen bir derleme için yayımcı ilkesi derlemesi oluşturmak üzere kullanılamediği, her zaman işlemci mimarisini belirttiğinden bu bir sonucudur.

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı Ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleme

Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için [genel derleme önbelleği aracını (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) kullanın.

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için

Komut istemine aşağıdaki komutu yazın:

```console
gacutil /i publisherPolicyAssemblyFile
```

Aşağıdaki komut, genel derleme önbelleğine `policy.1.0.myAssembly.dll` ekler.

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> Yayımcı ilkesi derlemesi, özgün yayımcı ilke dosyası derlemeyle aynı dizinde yer aldığı sürece genel derleme önbelleğine eklenemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlarla Programlama](../../standard/assembly/program.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](index.md)
- [Çalışma Zamanı Ayarları Şeması](./file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](./file-schema/index.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](redirect-assembly-versions.md)
