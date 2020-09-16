---
title: 'Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma'
description: Yapılandırma. Kayıtsız etkinleştirme için NET tabanlı COM bileşenleri. Kurulum bir Win32 stili uygulama bildirimi ve bir .NET bileşen bildirimi gerektirir.
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: ad25a79add84e43ba0a8e71a0f48c5ddf65108bd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554846"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma
.NET Framework tabanlı bileşenlere yönelik kayıt için ücretsiz etkinleştirme, COM bileşenleri için olduğundan biraz daha karmaşıktır. Kurulum için iki bildirim gerekir:  
  
- COM uygulamalarının, yönetilen bileşeni tanımlamak için bir Win32 stili uygulama bildirimi olması gerekir.  
  
- .NET Framework tabanlı bileşenlerin, çalışma zamanında gerekli etkinleştirme bilgileri için bir bileşen bildirimine sahip olması gerekir.  
  
 Bu konu, uygulama bildiriminin bir uygulamayla nasıl ilişkilendirileceğini açıklar; bileşen bildirimini bir bileşeniyle ilişkilendirin; ve bir derlemeye bileşen bildirimi ekleyin.  
  
## <a name="create-an-application-manifest"></a>Uygulama bildirimi oluşturma  
  
1. Bir XML Düzenleyicisi kullanarak, bir veya daha fazla yönetilen bileşenle birlikte bulunan COM uygulamasına ait uygulama bildirimini oluşturun (veya değiştirin).  
  
2. Aşağıdaki standart üstbilgiyi dosyanın başına ekleyin:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     Bildirim öğeleri ve öznitelikleri hakkında daha fazla bilgi için bkz. [uygulama bildirimleri](/windows/desktop/SbsCs/application-manifests).  
  
3. Bildirimin sahibini belirler. Aşağıdaki örnekte, `myComApp` Sürüm 1 bildirim dosyasının sahibidir.  
  
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
  
4. Bağımlı derlemeleri belirler. Aşağıdaki örnekte, `myComApp` öğesine bağımlıdır `myManagedComp` .  
  
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
  
5. Bildirim dosyasını kaydedin ve adlandırın. Uygulama bildiriminin adı, derleme yürütülebilir dosyasının ve ardından. manifest uzantısının adıdır. Örneğin, myComApp.exe için uygulama bildirimi dosya adı myComApp.exe. manifest ' dir.  
  
Uygulama bildirimini COM uygulamasıyla aynı dizine yükleyebilirsiniz. Alternatif olarak, uygulamayı uygulamanın. exe dosyasına bir kaynak olarak ekleyebilirsiniz. Daha fazla bilgi için bkz. [yan yana derlemeler hakkında](/windows/desktop/SbsCs/about-side-by-side-assemblies-).  
  
## <a name="create-a-component-manifest"></a>Bileşen bildirimi oluşturma  
  
1. XML Düzenleyicisi kullanarak, yönetilen derlemeyi betimleyen bir bileşen bildirimi oluşturun.  
  
2. Aşağıdaki standart üstbilgiyi dosyanın başına ekleyin:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. Dosyanın sahibini belirler. `<assemblyIdentity>` `<dependentAssembly>` Uygulama bildirimi dosyasındaki öğenin öğesi, bileşen bildiriminde bulunan ile aynı olmalıdır. Aşağıdaki örnekte, belirtilen `myManagedComp` Sürüm, bildirim dosyasının sahibidir.  
  
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
  
4. Derlemedeki her bir sınıfı belirler. `<clrClass>`Yönetilen derlemedeki her bir sınıfı benzersiz şekilde tanımlamak için öğesini kullanın. Öğesinin bir alt öğesi olan öğesi, `<assembly>` Aşağıdaki tabloda açıklanan özniteliklere sahiptir.  
  
    |Öznitelik|Açıklama|Gerekli|  
    |---------------|-----------------|--------------|  
    |`clsid`|Etkinleştirilecek sınıfı belirten tanımlayıcı.|Yes|  
    |`description`|Kullanıcıya bileşen hakkında bilgilendiren bir dize. Boş bir dize varsayılandır.|No|  
    |`name`|Yönetilen sınıfı temsil eden bir dize.|Yes|  
    |`progid`|Geç bağlantılı etkinleştirme için kullanılacak tanımlayıcı.|No|  
    |`threadingModel`|COM iş parçacığı modeli. "Her ikisi de varsayılan değerdir.|No|  
    |`runtimeVersion`|Kullanılacak ortak dil çalışma zamanı (CLR) sürümünü belirtir. Bu özniteliği belirtmezseniz ve CLR zaten yüklü değilse, bileşen CLR sürüm 4 ' ten önceki en son yüklenen CLR ile yüklenir. V 1.0.3705, v 1.1.4322 veya v 2.0.50727 belirtirseniz, sürüm CLR sürüm 4 ' ten (genellikle v 2.0.50727) önce yüklenen en son CLR sürümüne otomatik olarak kaydolur. CLR 'nin başka bir sürümü zaten yüklüyse ve belirtilen sürüm, işlem içi yan yana yüklenebiliyorsanız, belirtilen sürüm yüklenir; Aksi takdirde, yüklenen CLR kullanılır. Bu bir yükleme hatasına neden olabilir.|No|  
    |`tlbid`|Sınıf hakkında tür bilgilerini içeren tür kitaplığının tanımlayıcısı.|No|  
  
     Tüm öznitelik etiketleri büyük/küçük harfe duyarlıdır. OLE/COM ObjectViewer (Oleview.exe) ile derleme için aktarılmış tür kitaplığını görüntüleyerek CLSID, ProgID 'ler, iş parçacığı oluşturma modellerini ve çalışma zamanı sürümünü edinebilirsiniz.  
  
     Aşağıdaki bileşen bildirimi, ve olmak üzere iki sınıfı tanımlar `testClass1` `testClass2` .  
  
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
  
5. Bildirim dosyasını kaydedin ve adlandırın. Bir bileşen bildiriminin adı, derleme kitaplığının adı ve ardından. manifest uzantısını izler. Örneğin, myManagedComp.dll myManagedComp. manifest ' dir.  
  
 Bileşen bildirimini derlemede bir kaynak olarak katıştırmanız gerekir.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Yönetilen bir derlemede bir bileşen bildirimi eklemek için  
  
1. Aşağıdaki ifadeyi içeren bir kaynak betiği oluşturun:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     Bu bildirimde, `myManagedComp.manifest` eklenen bileşen bildiriminin adıdır. Bu örnek için, betik dosyası adı `myresource.rc` .  
  
2. Microsoft Windows Kaynak derleyicisi (Rc.exe) kullanarak betiği derleyin. Komut isteminde aşağıdaki komutu yazın:  
  
     `rc myresource.rc`  
  
     Rc.exe `myresource.res` kaynak dosyası üretir.  
  
3. Derlemenin kaynak dosyasını yeniden derleyin ve **/win32res** seçeneğini kullanarak kaynak dosyasını belirtin:  
  
    `/win32res:myresource.res`  
  
     Yine, `myresource.res` gömülü kaynakları içeren kaynak dosyasının adıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kayıtsız COM Birlikte Çalışma](registration-free-com-interop.md)
- [Kayıtsız COM birlikte çalışma gereksinimleri](/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Kayıt-ücretsiz etkinleştirme için COM bileşenlerini yapılandırma](/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Kayıt-ücretsiz etkinleştirmesi. NET tabanlı bileşenler: Izlenecek yol](/previous-versions/dotnet/articles/ms973915(v=msdn.10))
