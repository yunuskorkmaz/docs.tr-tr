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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: baabff187fb8a22aea37c4fb4c1dc11a680d3bb8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70853844"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma
.NET Framework tabanlı bileşenlere yönelik kayıt için ücretsiz etkinleştirme, COM bileşenleri için olduğundan biraz daha karmaşıktır. Kurulum için iki bildirim gerekir:  
  
- COM uygulamalarının, yönetilen bileşeni tanımlamak için bir Win32 stili uygulama bildirimi olması gerekir.  
  
- .NET Framework tabanlı bileşenlerin, çalışma zamanında gerekli etkinleştirme bilgileri için bir bileşen bildirimine sahip olması gerekir.  
  
 Bu konu, uygulama bildiriminin bir uygulamayla nasıl ilişkilendirileceğini açıklar; bileşen bildirimini bir bileşeniyle ilişkilendirin; ve bir derlemeye bileşen bildirimi ekleyin.  
  
### <a name="to-create-an-application-manifest"></a>Uygulama bildirimi oluşturmak için  
  
1. Bir XML Düzenleyicisi kullanarak, bir veya daha fazla yönetilen bileşenle birlikte bulunan COM uygulamasına ait uygulama bildirimini oluşturun (veya değiştirin).  
  
2. Aşağıdaki standart üstbilgiyi dosyanın başına ekleyin:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Bildirim öğeleri ve öznitelikleri hakkında daha fazla bilgi için bkz. [uygulama bildirimleri](/windows/desktop/SbsCs/application-manifests).  
  
3. Bildirimin sahibini belirler. Aşağıdaki örnekte, `myComApp` sürüm 1 bildirim dosyasının sahibidir.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4. Bağımlı derlemeleri belirler. Aşağıdaki örnekte, `myComApp` `myManagedComp`öğesine bağımlıdır.  
  
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
  
5. Bildirim dosyasını kaydedin ve adlandırın. Uygulama bildiriminin adı, derleme yürütülebilir dosyasının ve ardından. manifest uzantısının adıdır. Örneğin, myComApp. exe için uygulama bildirimi dosya adı myComApp. exe. manifest ' dir.  
  
 Uygulama bildirimini COM uygulamasıyla aynı dizine yükleyebilirsiniz. Alternatif olarak, uygulamayı uygulamanın. exe dosyasına bir kaynak olarak ekleyebilirsiniz. Daha fazla bilgi için bkz. [yan yana derlemeler hakkında](/windows/desktop/SbsCs/about-side-by-side-assemblies-).  
  
#### <a name="to-create-a-component-manifest"></a>Bileşen bildirimi oluşturmak için  
  
1. XML Düzenleyicisi kullanarak, yönetilen derlemeyi betimleyen bir bileşen bildirimi oluşturun.  
  
2. Aşağıdaki standart üstbilgiyi dosyanın başına ekleyin:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. Dosyanın sahibini belirler. Uygulama bildirimi dosyasındaki `<dependentAssembly>` öğenin öğesi,bileşenbildirimindebulunanileaynıolmalıdır.`<assemblyIdentity>` Aşağıdaki örnekte, belirtilen sürüm `myManagedComp` , bildirim dosyasının sahibidir.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4. Derlemedeki her bir sınıfı belirler. Yönetilen derlemedeki her bir sınıfı benzersiz şekilde tanımlamak için öğesinikullanın.`<clrClass>` `<assembly>` Öğesinin bir alt öğesi olan öğesi, aşağıdaki tabloda açıklanan özniteliklere sahiptir.  
  
    |Öznitelik|Açıklama|Gerekli|  
    |---------------|-----------------|--------------|  
    |`clsid`|Etkinleştirilecek sınıfı belirten tanımlayıcı.|Evet|  
    |`description`|Kullanıcıya bileşen hakkında bilgilendiren bir dize. Boş bir dize varsayılandır.|Hayır|  
    |`name`|Yönetilen sınıfı temsil eden bir dize.|Evet|  
    |`progid`|Geç bağlantılı etkinleştirme için kullanılacak tanımlayıcı.|Hayır|  
    |`threadingModel`|COM iş parçacığı modeli. "Her ikisi de varsayılan değerdir.|Hayır|  
    |`runtimeVersion`|Kullanılacak ortak dil çalışma zamanı (CLR) sürümünü belirtir. Bu özniteliği belirtmezseniz ve CLR zaten yüklü değilse, bileşen CLR sürüm 4 ' ten önceki en son yüklenen CLR ile yüklenir. V 1.0.3705, v 1.1.4322 veya v 2.0.50727 belirtirseniz, sürüm CLR sürüm 4 ' ten (genellikle v 2.0.50727) önce yüklenen en son CLR sürümüne otomatik olarak kaydolur. CLR 'nin başka bir sürümü zaten yüklüyse ve belirtilen sürüm, işlem içi yan yana yüklenebiliyorsanız, belirtilen sürüm yüklenir; Aksi takdirde, yüklenen CLR kullanılır. Bu bir yükleme hatasına neden olabilir.|Hayır|  
    |`tlbid`|Sınıf hakkında tür bilgilerini içeren tür kitaplığının tanımlayıcısı.|Hayır|  
  
     Tüm öznitelik etiketleri büyük/küçük harfe duyarlıdır. OLE/COM ObjectViewer (Oleview. exe) ile derleme için aktarılmış tür kitaplığını görüntüleyerek CLSID, ProgID 'ler, iş parçacığı modelleri ve çalışma zamanı sürümünü edinebilirsiniz.  
  
     Aşağıdaki bileşen bildirimi, ve `testClass1` `testClass2`olmak üzere iki sınıfı tanımlar.  
  
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
  
5. Bildirim dosyasını kaydedin ve adlandırın. Bir bileşen bildiriminin adı, derleme kitaplığının adı ve ardından. manifest uzantısını izler. Örneğin, myManagedComp. dll myManagedComp. manifest ' dir.  
  
 Bileşen bildirimini derlemede bir kaynak olarak katıştırmanız gerekir.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Yönetilen bir derlemede bir bileşen bildirimi eklemek için  
  
1. Aşağıdaki ifadeyi içeren bir kaynak betiği oluşturun:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     Bu bildirimde, `myManagedComp.manifest` eklenen bileşen bildiriminin adıdır. Bu örnek için, betik dosyası adı `myresource.rc`.  
  
2. Microsoft Windows Kaynak derleyicisi (RC. exe) kullanarak betiği derleyin. Komut satırında, aşağıdaki komutu yazın:  
  
     `rc myresource.rc`  
  
     RC. exe `myresource.res` kaynak dosyası üretir.  
  
3. Derlemenin kaynak dosyasını yeniden derleyin ve **/win32res** seçeneğini kullanarak kaynak dosyasını belirtin:  
  
    `/win32res:myresource.res`  
  
     Yine, `myresource.res` gömülü kaynakları içeren kaynak dosyasının adıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kayıtsız COM Birlikte Çalışma](registration-free-com-interop.md)
- [Kayıtsız COM birlikte çalışma gereksinimleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Kayıt-ücretsiz etkinleştirme için COM bileşenlerini yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Kayıt-ücretsiz etkinleştirmesi. NET tabanlı bileşenler: Bir Izlenecek yol](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))
