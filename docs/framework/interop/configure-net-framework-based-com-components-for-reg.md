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
ms.openlocfilehash: c8f78e926835e86fdc20da5e4e1bc66c4b6ab1a2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625448"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma
Kayıtsız etkinleştirme için .NET Framework tabanlı bileşenler, yalnızca COM bileşenleri için olandan biraz daha karmaşık. Kurulum, iki bildirimleri gerektirir:  
  
- COM uygulamaları yönetilen bileşen tanımlamak için bir Win32 stili bildiriminin olması gerekir.  
  
- .NET framework tabanlı bileşenler, bileşen bildirimini etkinleştirme bilgi çalışma zamanında gereken olması gerekir.  
  
 Bu konu, bir uygulama bildirimi uygulamayla ilişkilendirilecek açıklar; Bileşen bildirimi, bir bileşeniyle ilişkilendirme; ' i tıklatın ve bileşeni bildirimini derlemede katıştırmak.  
  
### <a name="to-create-an-application-manifest"></a>Bir uygulama bildirimi oluşturmak için  
  
1. Bir XML Düzenleyicisi'ni kullanarak oluşturun (veya değiştirme) bir veya daha fazla yönetilen bileşenleri ile birlikte COM uygulama sahibi uygulama bildirimi.  
  
2. Aşağıdaki standart üstbilgi dosyasının başına ekleyin:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Liste öğelerini ve onların öznitelikleri hakkında daha fazla bilgi için bkz. [uygulama bildirimleri](/windows/desktop/SbsCs/application-manifests).  
  
3. Bildirimin sahibi olacak kişileri tanımlayın. Aşağıdaki örnekte, `myComApp` sürüm 1 sahip bildirim dosyası.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4. Bağımlı derlemelerin belirleyin. Aşağıdaki örnekte, `myComApp` bağlıdır `myManagedComp`.  
  
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
  
5. Kaydet ve bildirim dosyasının adı. Bir uygulama bildirimi yürütülebilir derlemenin adını .manifest uzantısı tarafından izlenen adıdır. Örneğin, uygulama bildirim dosyası myComApp.exe myComApp.exe.manifest adıdır.  
  
 Bir uygulama bildirimi, COM uygulama ile aynı dizinde yükleyebilirsiniz. Alternatif olarak, bunu bir kaynak olarak uygulamanın .exe dosyasına ekleyebilirsiniz. Daha fazla bilgi için ek bilgi için bkz. [yan yana derlemeler hakkında](/windows/desktop/SbsCs/about-side-by-side-assemblies-).  
  
#### <a name="to-create-a-component-manifest"></a>Bileşen bildirimi oluşturmak için  
  
1. Bir XML Düzenleyicisi'ni kullanarak yönetilen derlemeyi tanımlamak için bir bileşen bildirimi oluşturun.  
  
2. Aşağıdaki standart üstbilgi dosyasının başına ekleyin:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. Dosyanın sahibi olacak kişileri tanımlayın. `<assemblyIdentity>` Öğesinin `<dependentAssembly>` bileşen bildirimini bir uygulama bildirimi dosyasındaki öğesi eşleşmesi gerekir. Aşağıdaki örnekte, `myManagedComp` sürüm 1.2.3.4 sahip bildirim dosyası.  
  
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
  
4. Derlemedeki her bir sınıf tanımlar. Kullanım `<clrClass>` her derlemede sınıfı, yönetilen benzersiz olarak tanımlanabilmesi için öğesi. Bir alt öğesi olan öğe, `<assembly>` öğesi, aşağıdaki tabloda açıklanan öznitelikleri.  
  
    |Öznitelik|Açıklama|Gerekli|  
    |---------------|-----------------|--------------|  
    |`clsid`|Belirten etkinleştirilmesi için sınıf tanımlayıcısı.|Evet|  
    |`description`|Kullanıcı bileşeni hakkında bilgilendiren bir dize. Boş bir dize varsayılandır.|Hayır|  
    |`name`|Yönetilen sınıf temsil eden bir dize.|Evet|  
    |`progid`|Geç bağlama etkinleştirmesi için kullanılan tanımlayıcı.|Hayır|  
    |`threadingModel`|COM iş parçacığı modeli. "Both" varsayılan değerdir.|Hayır|  
    |`runtimeVersion`|Kullanılacak ortak dil çalışma zamanı (CLR) sürümünü belirtir. Bu özniteliği belirtmezseniz ve CLR zaten yüklü değilse, bileşen CLR sürüm 4 önce en son yüklenen CLR ile yüklenir. V1.0.3705, v1.1.4322 veya v2.0.50727 belirtirseniz, sürüm otomatik olarak ilet için en son yüklenen CLR sürümü CLR sürüm 4 (genellikle v2.0.50727) önce yapar. Başka bir CLR sürümü zaten yüklü olan ve belirtilen sürümü işlemdeki yan yana yüklenebilir, belirtilen sürümü yüklenir; Aksi takdirde, yüklü CLR kullanılır. Bu yük başarısız olmasına neden.|Hayır|  
    |`tlbid`|Sınıf türü bilgilerini içeren tür kitaplığının tanımlayıcı.|Hayır|  
  
     Tüm öznitelik etiketler büyük/küçük harfe duyarlıdır. CLSID, ProgIDs, modelleri ve çalışma zamanı sürümü, dışarı aktarılan tür kitaplığını derleme OLE/COM ObjectViewer (Oleview.exe) ile görüntüleyerek iş parçacığı elde edebilirsiniz.  
  
     İki sınıf aşağıdaki bileşen bildirimini tanımlar `testClass1` ve `testClass2`.  
  
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
  
5. Kaydet ve bildirim dosyasının adı. Bir bileşen bildirimini .manifest uzantısı tarafından izlenen derleme kitaplığının adı adıdır. Örneğin, myManagedComp.dll myManagedComp.manifest olur.  
  
 Bir kaynak olarak bileşen bildirimini derlemesinde katıştırmanız gerekir.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Yönetilen derlemede bir bileşen bildirimi eklemek için  
  
1. Aşağıdaki deyim içeren bir kaynak betiği oluşturun:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     Bu bildirimde `myManagedComp.manifest` katıştırılmış bileşen bildirimini adıdır. Bu örnekte, betik dosyası adı `myresource.rc`.  
  
2. Microsoft Windows Kaynak derleyicisi (Rc.exe) kullanarak betiği derleyin. Komut satırında, aşağıdaki komutu yazın:  
  
     `rc myresource.rc`  
  
     RC.exe üretir `myresource.res` kaynak dosyası.  
  
3. Derlemenin kaynak dosyasını yeniden derleyin ve kullanarak kaynak dosyayı belirtin **/win32res** seçeneği:  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     Yeniden `myresource.res` gömülü kaynak içeren kaynak dosyasının adıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kayıtsız COM Birlikte Çalışma](registration-free-com-interop.md)
- [Kayıtsız COM birlikte çalışma için gereksinimler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Kayıtsız etkinleştirme için COM bileşenlerini yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Kayıtsız etkinleştirme. AĞ tabanlı bileşenler: İzlenecek yollar](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))
