---
title: 'Nasıl yapılır: Yayımcı İlkesi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3fdc3786be3307e8c882a33b5139ee34344733b8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504824"
---
# <a name="how-to-create-a-publisher-policy"></a>Nasıl yapılır: Yayımcı İlkesi Oluşturma
Derleme satıcıları, uygulamaları yükseltilen derlemeye bir yayımcı ilkesi dosyası dahil ederek bir derlemenin daha yeni bir sürümünü kullanacağını durumu. Yayımcı ilkesi dosyası, derleme yeniden yönlendirmesini ve kod temel ayarları belirtir ve bir uygulama yapılandırma dosyası aynı biçimi kullanır. Yayımcı ilkesi dosyası bir bütünleştirilmiş kod içine derlenmiş ve genel bütünleştirilmiş kod önbelleğine yerleştirilmesi.  
  
 Yayımcı ilkesi oluşturmak için gerekli olan üç adım vardır:  
  
1.  Yayımcı ilkesi dosyası oluşturun.  
  
2.  Yayımcı ilke derlemesi oluşturun.  
  
3.  Yayımcı ilke derlemesi genel derleme önbelleğine ekleme.  
  
 Yayımcı ilkesi için şema açıklanan [derleme sürümlerini yeniden yönlendirme](../../../docs/framework/configure-apps/redirect-assembly-versions.md). Aşağıdaki örnek, bir yayımcı gösterir. bir sürümü yönlendiren ilke dosyası `myAssembly` diğerine.  
  
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
  
 Bir kod tabanına belirleme konusunda bilgi edinmek için [bir derlemenin konumunu belirtme](../../../docs/framework/configure-apps/specify-assembly-location.md).  
  
## <a name="creating-the-publisher-policy-assembly"></a>Yayımcı ilke derlemesi oluşturma  
 Kullanım [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) yayımcı ilke derlemesi oluşturmak için.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Yayımcı ilke derlemesi oluşturmak için  
  
1.  Komut isteminde aşağıdaki komutu yazın:  
  
     **Al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:**  *keyPairFile* **/Platform:** *processorArchitecture*  
  
     Bu komutta:  
  
    -   *PublisherPolicyFile* bağımsız yayımcı ilkesi dosyası adıdır.  
  
    -   *PublisherPolicyAssemblyFile* bağımsız değişkeni, bu komutu sonuçları yayımcı ilke derlemesi adıdır. Derleme dosya adı biçimi izlemelidir:  
  
         **ilke.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   *KeyPairFile* bağımsız değişkeni anahtar çiftini içeren dosyanın adıdır. Derleme ve yayımcı ilke derlemesi aynı anahtar çifti ile oturum açması gerekir.  
  
    -   *ProcessorArchitecture* bağımsız değişkeni bir işlemciye özel derleme tarafından hedeflenen platformun tanımlar.  
  
        > [!NOTE]
        >  Belirli bir işlemci mimarisini hedefleyen olanağı, .NET Framework 2.0 sürümünde yenidir.  
  
     Aşağıdaki komut, adı verilen bir yayımcı ilke derlemesi oluşturur `policy.1.0.myAssembly` Yayımcı ilkesi dosyası olarak adlandırılan `pub.config`, içindeki anahtar çifti kullanarak derlemeyi tanımlayıcı bir ad atar `sgKey.snk` dosya ve derleme x86 hedefleyen belirtir İşlemci mimarisi.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     Yayımcı ilke derlemesi için geçerli bir derlemenin İşlemci mimarisi eşleşmesi gerekir. Bu nedenle, derlemenizin varsa bir <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> değerini <xref:System.Reflection.ProcessorArchitecture.MSIL>, o derleme için yayımcı ilke derlemesi ile oluşturulmalıdır `/platform:anycpu`. Ayrı bir sağlamanız gereken her işlemciye özel derleme için yayımcı ilke derlemesi.  
  
     Yeni bir yayımcı ilke derlemesi doğru işlemci mimarisini ile sağlayabilirsiniz bu kural bir sonucu bir derleme için İşlemci mimarisi değiştirmek için sürüm numarasının büyük veya küçük bileşen değiştirmeniz gerekir, böylelikle. Derlemenizi farklı bir işlemci mimarisine olduğunda eski yayımcı ilke derlemesi, derlemenizi hizmet veremiyor.  
  
     Başka bir sonucu, sürüm 2.0 bağlayıcı İşlemci mimarisi her zaman belirttiğinden .NET Framework'ün önceki sürümleri kullanılarak derlenmiş bir derleme için bir yayımcı ilke derlemesi oluşturmak için kullanılamaz olur.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı ilke derlemesi genel derleme önbelleğine ekleme  
 Kullanım [Genel Derleme Önbelleği aracını (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) yayımcı ilke derlemesi genel derleme önbelleğine eklemek için.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı ilke derlemesi genel derleme önbelleğine eklemek için  
  
1.  Komut isteminde aşağıdaki komutu yazın:  
  
     **Gacutil /i***publisherPolicyAssemblyFile*  
  
     Aşağıdaki komut ekler `policy.1.0.myAssembly.dll` için Genel Derleme Önbelleği.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  Özgün Yayımcı ilkesi dosyası derleme olarak aynı dizinde bulunan sürece, yayımcı ilke derlemesi genel derleme önbelleğine eklenemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Uygulamaları Yapılandırma](../../../docs/framework/configure-apps/index.md)  
 [.NET Framework uygulamalarını yapılandırma](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Çalışma Zamanı Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
