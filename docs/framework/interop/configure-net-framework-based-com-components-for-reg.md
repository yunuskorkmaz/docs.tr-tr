---
title: 'Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: 9e273bd3e4bf2bb6945fe48c850783a54fa9a869
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291750"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma
.NET Framework tabanlı bileşenler için kayıt gerektirmeden etkinleştirme, COM bileşenlerine göre yalnızca biraz daha karmaşıktır. Kurulum iki bildirim gerektirir:  
  
- COM uygulamaları, yönetilen bileşeni tanımlamak için Win32 tarzı bir uygulama bildirimine sahip olmalıdır.  
  
- .NET Framework tabanlı bileşenler, çalışma zamanında gerekli etkinleştirme bilgileri için bir bileşen manifestosuna sahip olmalıdır.  
  
 Bu konu, bir uygulama bildiriminin bir uygulamayla nasıl ilişkilendirilen; bileşen bildirimini bir bileşenle ilişkilendirin; ve bir bileşen bildirimini bir derlemeye katıştırın.  
  
## <a name="create-an-application-manifest"></a>Uygulama bildirimi oluşturma  
  
1. Bir XML düzenleyicisi kullanarak, com uygulamasının sahip olduğu ve bir veya daha fazla yönetilen bileşenle birlikte çalışan uygulama bildirimini oluşturun (veya değiştirin).  
  
2. Dosyanın başına aşağıdaki standart üstbilgi ekleyin:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     Bildirim öğeleri ve öznitelikleri hakkında bilgi için [Uygulama Bildirimleri'ne](/windows/desktop/SbsCs/application-manifests)bakın.  
  
3. Bildirimin sahibini tanımlayın. Aşağıdaki örnekte, `myComApp` sürüm 1 manifesto dosyasının sahibidir.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />
    </assembly>  
    ```  
  
4. Bağımlı derlemeleri tanımlayın. Aşağıdaki örnekte, `myComApp` `myManagedComp`bağlıdır.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="x86"
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myManagedComp"
                        version="6.0.0.0"
                        processorArchitecture="X86"
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. Bildirim dosyasını kaydedin ve adlandırın. Bir uygulama bildiriminin adı, .manifest uzantısı tarafından izlenen yürütülebilir derlemenin adıdır. Örneğin, myComApp.exe için uygulama bildirimi dosya adı myComApp.exe.manifest olduğunu.  
  
Com uygulamasıyla aynı dizinde bir uygulama bildirimi yükleyebilirsiniz. Alternatif olarak, uygulamanın .exe dosyasına kaynak olarak ekleyebilirsiniz. Daha fazla bilgi için Yan [Yana Montajlar Hakkında'ya](/windows/desktop/SbsCs/about-side-by-side-assemblies-)bakın.  
  
## <a name="create-a-component-manifest"></a>Bileşen bildirimi oluşturma  
  
1. Bir XML düzenleyicisi kullanarak, yönetilen derlemeyi açıklamak için bir bileşen bildirimi oluşturun.  
  
2. Dosyanın başına aşağıdaki standart üstbilgi ekleyin:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. Dosyanın sahibini tanımlayın. Uygulama `<assemblyIdentity>` bildirimi `<dependentAssembly>` dosyasındaki öğe öğesi, bileşen bildirimindeki öğeyle eşleşmelidir. Aşağıdaki örnekte, `myManagedComp` sürüm 1.2.3.4 bildirim dosyasının sahibidir.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />
    </assembly>
    ```  
  
4. Derlemedeki her sınıfı tanımlayın. Yönetilen `<clrClass>` derlemedeki her sınıfı benzersiz olarak tanımlamak için öğeyi kullanın. Öğenin `<assembly>` bir alt öğesi olan öğe, aşağıdaki tabloda açıklanan özniteliklere sahiptir.  
  
    |Öznitelik|Açıklama|Gerekli|  
    |---------------|-----------------|--------------|  
    |`clsid`|Sınıfın etkinleştirilecek lerini belirten tanımlayıcı.|Evet|  
    |`description`|Kullanıcıyı bileşen hakkında bilgilendiren bir dize. Boş bir dize varsayılandır.|Hayır|  
    |`name`|Yönetilen sınıfı temsil eden bir dize.|Evet|  
    |`progid`|Geç bağlanan etkinleştirme için kullanılacak tanımlayıcı.|Hayır|  
    |`threadingModel`|COM iş parçacığı modeli. "Her ikisi de" varsayılan değerdir.|Hayır|  
    |`runtimeVersion`|Kullanılacak ortak dil çalışma zamanı (CLR) sürümünü belirtir. Bu özniteliği belirtmezseniz ve CLR zaten yüklenmemişse, bileşen CLR sürüm 4'ten önce en son yüklenen CLR ile yüklenir. V1.0.3705, v1.1.4322 veya v2.0.50727 belirtirseniz, sürüm otomatik olarak CLR sürüm 4 'den önce (genellikle v2.0.50727) en son yüklenen CLR sürümüne geçilir. CLR'nin başka bir sürümü zaten yüklenmişse ve belirtilen sürüm işlem içinde yan yana yüklenebilirse, belirtilen sürüm yüklenir; aksi takdirde, yüklenen CLR kullanılır. Bu bir yük hatasına neden olabilir.|Hayır|  
    |`tlbid`|Sınıf hakkında tür bilgileri içeren tür kitaplığı tanımlayıcısı.|Hayır|  
  
     Tüm öznitelik etiketleri büyük/küçük harf duyarlıdır. OLE/COM ObjectViewer (Oleview.exe) ile derleme için dışa aktarılan tür kitaplığını görüntüleyerek CLSID'leri, ProgID'leri, iş parçacığı modellerini ve çalışma zamanı sürümünü edinebilirsiniz.  
  
     Aşağıdaki bileşen bildirimi iki `testClass1` sınıf `testClass2`tanımlar ve .  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. Bildirim dosyasını kaydedin ve adlandırın. Bileşen bildiriminin adı, .manifest uzantısı tarafından izlenen derleme kitaplığı adıdır. Örneğin, myManagedComp.dll myManagedComp.manifest olduğunu.  
  
 Bileşen bildirimini derlemeye kaynak olarak gömmeniz gerekir.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Yönetilen bir derlemeye bileşen bildirimini gömmek için  
  
1. Aşağıdaki deyimi içeren bir kaynak komut dosyası oluşturun:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     Bu ifadede, `myManagedComp.manifest` gömülü olan bileşen bildiriminin adıdır. Bu örnekte, komut dosyası `myresource.rc`dosya adı.  
  
2. Microsoft Windows Kaynak Derleyicisini (Rc.exe) kullanarak komut dosyasını derleyin. Komut isteminde aşağıdaki komutu yazın:  
  
     `rc myresource.rc`  
  
     Rc.exe kaynak `myresource.res` dosyasını üretir.  
  
3. Derlemenin kaynak dosyasını yeniden derleyin ve **/win32res** seçeneğini kullanarak kaynak dosyasını belirtin:  
  
    `/win32res:myresource.res`  
  
     Yine, `myresource.res` katıştırılmış kaynakları içeren kaynak dosyasının adıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kayıtsız COM Birlikte Çalışma](registration-free-com-interop.md)
- [Kayıt-Free COM Interop için Gereksinimleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Kayıt-Free Aktivasyon için COM Bileşenlerinin Yapılandırılması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Kayıt-Free Aktivasyonu . NET Tabanlı Bileşenler: Bir Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))
