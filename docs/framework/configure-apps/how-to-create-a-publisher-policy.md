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
ms.openlocfilehash: 91971e4d41c3a54fa72ae73a3655dab650019676
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758132"
---
# <a name="how-to-create-a-publisher-policy"></a>Nasıl yapılır: Yayımcı İlkesi Oluşturma
Derlemeleri satıcıları yükseltilmiş derleme Yayımcı ilkesi dosyasıyla dahil ederek uygulamalar derleme daha yeni bir sürümü kullanmalıdır durumu. Yayımcı ilkesi dosyası derleme yeniden yönlendirme ve kod temel ayarları belirtir ve bir uygulama yapılandırma dosyası olarak ile aynı biçimi kullanır. Yayımcı ilkesi dosyası bütünleştirilmiş koda derlenmemiş ve genel derleme önbelleğinde yerleştirilir.  
  
 Bir yayımcı ilkesi oluşturmaya dahil üç adım vardır:  
  
1.  Bir yayımcı ilkesi dosyası oluşturun.  
  
2.  Yayımcı ilke derlemesi oluşturun.  
  
3.  Yayımcı ilke derlemesi genel derleme önbelleğine ekleme.  
  
 Yayımcı ilkesi için şemayı açıklanan [derleme sürümlerini yönlendirme](../../../docs/framework/configure-apps/redirect-assembly-versions.md). Aşağıdaki örnek, bir yayımcı gösterir bir sürümü yönlendiren ilke dosyası `myAssembly` başka bir.  
  
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
  
 Kod temeliniz belirleme konusunda bilgi edinmek için [bir derlemenin konumunu belirtme](../../../docs/framework/configure-apps/specify-assembly-location.md).  
  
## <a name="creating-the-publisher-policy-assembly"></a>Yayımcı ilke derlemesi oluşturma  
 Kullanım [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) yayımcı ilke derlemesi oluşturulamadı.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Yayımcı ilke derlemesi oluşturmak için  
  
1.  Komut isteminde aşağıdaki komutu yazın:  
  
     **Al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:**  *keyPairFile* **/Platform:** *processorArchitecture*  
  
     Bu komutta:  
  
    -   *PublisherPolicyFile* bağımsız yayımcı ilkesi dosyanın adıdır.  
  
    -   *PublisherPolicyAssemblyFile* bağımsız değişkeni, bu komutu sonuçları yayımcı ilke derlemesi adıdır. Derleme dosya adı biçime uymalıdır:  
  
         **ilke.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   *KeyPairFile* bağımsız değişkeni, anahtar çiftini içeren dosyanın adıdır. Derleme ve yayımcı ilke derlemesi aynı anahtar çifti ile oturum açmanız gerekir.  
  
    -   *ProcessorArchitecture* bağımsız değişkeni bir işlemciye özgü derlemesi tarafından hedeflenen platform tanımlar.  
  
        > [!NOTE]
        >  Belirli bir işlemci mimarisi hedef olanağı, .NET Framework 2.0 sürümünde yenidir.  
  
     Aşağıdaki komut adlı yayımcı ilke derlemesi oluşturur `policy.1.0.myAssembly` bir yayımcı ilkesi dosyasından adlı `pub.config`, bir güçlü ad anahtar çifti kullanarak derlemeyi atar `sgKey.snk` dosya ve derleme x86 hedefler belirtir İşlemci mimarisi.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     Yayımcı ilke derlemesi uygulandığı derleme işlemci mimarisinden eşleşmesi gerekir. Bu nedenle, derlemenizi varsa bir <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> değerini <xref:System.Reflection.ProcessorArchitecture.MSIL>, bu derleme için yayımcı ilke derlemesi ile oluşturulmalıdır `/platform:anycpu`. Ayrı bir sağlamalısınız yayımcı ilke derlemesi her işlemci özgü derleme için.  
  
     Yeni bir yayımcı ilke derlemesi doğru işlemci mimarisini ile sağladığınız sonucu bu kuralın İşlemci mimarisi için derlemeyi değiştirmek için birincil veya ikincil sürüm numarası bileşeni değiştirmeniz gerekir, böylelikle. Farklı bir işlemci mimarisine derlemenizi sonra eski yayımcı ilke derlemesi derlemenizi hizmet veremiyor.  
  
     Başka bir sonuç sürüm 2.0 bağlayıcı yayımcı ilke derlemesi için .NET Framework'ün önceki sürümlerini kullanan her zaman İşlemci mimarisi belirttiğinden derlenmiş bir derlemeyi oluşturmak için kullanılamaz olur.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı ilke derlemesi genel derleme önbelleğine ekleme  
 Kullanım [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) yayımcı ilke derlemesi genel derleme önbelleğine eklemek için.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Yayımcı ilke derlemesi genel derleme önbelleğine eklemek için  
  
1.  Komut isteminde aşağıdaki komutu yazın:  
  
     **Gacutil /i***publisherPolicyAssemblyFile*   
  
     Aşağıdaki komut ekler `policy.1.0.myAssembly.dll` genel derleme önbelleği için.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  Özgün Yayımcı ilkesi dosyası derleme aynı dizinde bulunan sürece yayımcı ilke derlemesi genel derleme önbelleğine eklenemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Uygulamaları Yapılandırma](../../../docs/framework/configure-apps/index.md)  
 [.NET Framework uygulamaları yapılandırma](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Çalışma Zamanı Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
