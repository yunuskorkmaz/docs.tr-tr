---
title: 'Nasıl yapılır: Yayımcı İlkesi Oluşturma'
description: Derleme satıcılarının, uygulamaların daha yeni sürümü kullanması gerektiğini öğrenmek için .NET 'teki yükseltilmiş bir derleme ile bir yayımcı ilke dosyası oluşturma hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 23e9d8144ec5742e0371d566b7af59dc9dd30c9b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105409"
---
# <a name="how-to-create-a-publisher-policy"></a>Nasıl yapılır: Yayımcı İlkesi Oluşturma

Derlemelerin satıcıları, yükseltilen derlemeye bir yayımcı ilke dosyası ekleyerek uygulamaların bir derlemenin daha yeni bir sürümünü kullanması gerektiğini belirtebilir. Yayımcı ilke dosyası, derleme yeniden yönlendirme ve kod tabanı ayarlarını belirtir ve bir uygulama yapılandırma dosyası ile aynı biçimi kullanır. Yayımcı ilke dosyası bir derlemede derlenir ve genel derleme önbelleğine yerleştirilir.

Yayımcı ilkesi oluşturma ile ilgili üç adım vardır:

1. Bir yayımcı ilke dosyası oluşturun.

2. Yayımcı ilkesi derlemesi oluşturun.

3. Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleyin.

Yayımcı ilkesi şeması, [derleme sürümlerini yeniden yönlendirme](redirect-assembly-versions.md)bölümünde açıklanmıştır. Aşağıdaki örnek, bir sürümünü diğerine yönlendiren bir yayımcı ilkesi dosyası gösterir `myAssembly` .

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

Yayımcı ilke derlemesini oluşturmak için [Derleme Bağlayıcı (Al.exe)](../tools/al-exe-assembly-linker.md) kullanın.

#### <a name="to-create-a-publisher-policy-assembly"></a>Yayımcı ilkesi derlemesi oluşturmak için

Komut istemine aşağıdaki komutu yazın:

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

Şu komutta:

- `publisherPolicyFile`Bağımsız değişkeni Yayımcı ilke dosyasının adıdır.

- `publisherPolicyAssemblyFile`Bağımsız değişkeni, bu komutun sonucu olan yayımcı ilke derlemesinin adıdır. Derleme dosyası adı şu biçimde olmalıdır:

  'policy.majorNumber.minorNumber.mainAssemblyName.dll '

- `keyPairFile`Bağımsız değişkeni, anahtar çiftini içeren dosyanın adıdır. Derleme ve Yayımcı ilke derlemesini aynı anahtar çiftiyle imzalamanız gerekir.

- `processorArchitecture`Bağımsız değişkeni, işlemciye özgü bir derleme tarafından hedeflenen platformu tanımlar.

  > [!NOTE]
  > Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework 2,0 ' den başlayarak kullanılabilir.

Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework 2,0 ' den başlayarak kullanılabilir. Aşağıdaki komut, adlı bir yayımcı ilke dosyasından çağrılan bir yayımcı ilkesi derlemesi oluşturur `policy.1.0.myAssembly` `pub.config` , dosyadaki anahtar çiftini kullanarak derlemeye tanımlayıcı bir ad atar `sgKey.snk` ve derlemenin x86 işlemci mimarisini hedeflediğini belirtir.

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

Yayımcı ilke derlemesinin, uygulandığı derlemenin işlemci mimarisiyle eşleşmesi gerekir. Bu nedenle, derlemenizin bir <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> değeri varsa <xref:System.Reflection.ProcessorArchitecture.MSIL> , bu derleme için yayımcı ilke derlemesinin ile oluşturulması gerekir `/platform:anycpu` . İşlemciye özgü her derleme için ayrı bir yayımcı ilke derlemesi sağlamalısınız.

Bu kuralın bir sonucu, bir derlemenin işlemci mimarisini değiştirmek için, sürüm numarasının büyük veya küçük bileşenini değiştirmeniz, böylece doğru işlemci mimarisine sahip yeni bir yayımcı ilke derlemesi sağlayabilmeniz gerekir. Derlemelerinizin farklı bir işlemci mimarisi varsa, eski yayımcı ilkesi derlemesi derlemenizi kullanamaz.

Bunun nedeni, sürüm 2,0 bağlayıcının, .NET Framework önceki sürümleri kullanılarak derlenen bir derleme için yayımcı ilkesi derlemesi oluşturmak üzere kullanılamediği, her zaman işlemci mimarisini belirttiğinden bu bir sonucudur.

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı Ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleme

Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için [genel derleme önbelleği aracını (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) kullanın.

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için

Komut istemine aşağıdaki komutu yazın:

```console
gacutil /i publisherPolicyAssemblyFile
```

Aşağıdaki komut, `policy.1.0.myAssembly.dll` genel derleme önbelleğine ekler.

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> Bağımsız değişkende belirtilen özgün yayımcı ilkesi dosyası `/link` derlemeyle aynı dizinde yer aldığı sürece Yayımcı ilkesi derlemesi genel derleme önbelleğine eklenemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemelerle Programlama](../../standard/assembly/index.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma](index.md)
- [Çalışma zamanı ayarları şeması](./file-schema/runtime/index.md)
- [Yapılandırma dosyası şeması](./file-schema/index.md)
- [Derleme Sürümlerini Yönlendirme](redirect-assembly-versions.md)
