---
title: 'Nasıl yapılır: Yayımcı İlkesi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: bf5b55eb01a31106fcc7cb0d79212416ab0c898d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913055"
---
# <a name="how-to-create-a-publisher-policy"></a>Nasıl yapılır: Yayımcı İlkesi Oluşturma
Derlemelerin satıcıları, yükseltilen derlemeye bir yayımcı ilke dosyası ekleyerek uygulamaların bir derlemenin daha yeni bir sürümünü kullanması gerektiğini belirtebilir. Yayımcı ilke dosyası, derleme yeniden yönlendirme ve kod tabanı ayarlarını belirtir ve bir uygulama yapılandırma dosyası ile aynı biçimi kullanır. Yayımcı ilke dosyası bir derlemede derlenir ve genel derleme önbelleğine yerleştirilir.  
  
 Yayımcı ilkesi oluşturma ile ilgili üç adım vardır:  
  
1. Bir yayımcı ilke dosyası oluşturun.  
  
2. Yayımcı ilkesi derlemesi oluşturun.  
  
3. Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleyin.  
  
 Yayımcı ilkesi şeması, [derleme sürümlerini yeniden yönlendirme](redirect-assembly-versions.md)bölümünde açıklanmıştır. Aşağıdaki örnek, bir sürümünü `myAssembly` diğerine yönlendiren bir yayımcı ilkesi dosyası gösterir.  
  
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
  
1. Komut istemine aşağıdaki komutu yazın:  
  
     **Al/Link:** *publisherPolicyFile* **/Out:** *Publisherpolicyassemblyfile* **/keyfile:** *keyPairFile* **/Platform:** *ProcessorArchitecture*  
  
     Bu komutta:  
  
    - *PublisherPolicyFile* bağımsız değişkeni, yayımcı ilkesi dosyasının adıdır.  
  
    - *Publisherpolicyassemblyfile* bağımsız değişkeni, bu komutun sonucu olan yayımcı ilkesi derlemesinin adıdır. Derleme dosyası adı şu biçimde olmalıdır:  
  
         **ilkesinin.** *Majornumber* **.** *minorNumber* **.** *ana AssemblyName* **. dll**  
  
    - *KeyPairFile* bağımsız değişkeni, anahtar çiftini içeren dosyanın adıdır. Derleme ve Yayımcı ilke derlemesini aynı anahtar çiftiyle imzalamanız gerekir.  
  
    - *ProcessorArchitecture* bağımsız değişkeni, işlemciye özgü bir derleme tarafından hedeflenen platformu tanımlar.  
  
        > [!NOTE]
        >  Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework sürüm 2,0 ' de yenidir.  
  
     Aşağıdaki komut, adlı `policy.1.0.myAssembly` `pub.config`bir yayımcı ilke dosyasından çağrılan bir yayımcı ilkesi derlemesi oluşturur, `sgKey.snk` dosyadaki anahtar çiftini kullanarak derlemeye tanımlayıcı bir ad atar ve derlemenin x86 'yi hedeflediğini belirtir işlemci mimarisi.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     Yayımcı ilke derlemesinin, uygulandığı derlemenin işlemci mimarisiyle eşleşmesi gerekir. Bu nedenle, derlemenizin bir <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> <xref:System.Reflection.ProcessorArchitecture.MSIL>değeri varsa, bu derleme için yayımcı ilke derlemesinin ile `/platform:anycpu`oluşturulması gerekir. İşlemciye özgü her derleme için ayrı bir yayımcı ilke derlemesi sağlamalısınız.  
  
     Bu kuralın bir sonucu, bir derlemenin işlemci mimarisini değiştirmek için, sürüm numarasının büyük veya küçük bileşenini değiştirmeniz, böylece doğru işlemci mimarisine sahip yeni bir yayımcı ilke derlemesi sağlayabilmeniz gerekir. Derlemelerinizin farklı bir işlemci mimarisi varsa, eski yayımcı ilkesi derlemesi derlemenizi kullanamaz.  
  
     Bunun nedeni, sürüm 2,0 bağlayıcının, .NET Framework önceki sürümleri kullanılarak derlenen bir derleme için yayımcı ilkesi derlemesi oluşturmak üzere kullanılamediği, her zaman işlemci mimarisini belirttiğinden bu bir sonucudur.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı Ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleme  
 Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için [genel derleme önbelleği aracını (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) kullanın.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için  
  
1. Komut istemine aşağıdaki komutu yazın:  
  
     **Gacutil /i** *publisherPolicyAssemblyFile*  
  
     Aşağıdaki komut, genel `policy.1.0.myAssembly.dll` derleme önbelleğine ekler.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  Yayımcı ilkesi derlemesi, özgün yayımcı ilke dosyası derlemeyle aynı dizinde yer aldığı sürece genel derleme önbelleğine eklenemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlarla Programlama](../app-domains/programming-with-assemblies.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](index.md)
- [Çalışma Zamanı Ayarları Şeması](./file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](./file-schema/index.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](redirect-assembly-versions.md)
