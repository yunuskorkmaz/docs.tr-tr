---
title: "Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fdae288650a0ff7b1a34b3a38a231d3da6caf560
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma
Kayıtsız etkinleştirme için .NET Framework tabanlı bileşenler, yalnızca COM bileşenleri olandan biraz daha karmaşık. Kurulum, iki bildirimleri gerektirir:  
  
-   COM uygulamaları yönetilen bileşen tanımlamak için bir Win32 stili uygulama bildirimi olması gerekir.  
  
-   .NET framework tabanlı bileşenler çalışma zamanında gereken etkinleştirme bilgileri için bileşen bildirimi olması gerekir.  
  
 Bu konu, bir uygulama bildirimi uygulamayla ilişkilendirmek açıklar; Bileşen bildirimi bir bileşeniyle ilişkilendirme; ve bileşen bildirimi derlemede katıştırmak.  
  
### <a name="to-create-an-application-manifest"></a>Bir uygulama bildirimi oluşturmak için  
  
1.  Bir XML Düzenleyicisi'ni kullanarak oluşturun (veya değiştirme) bir veya daha fazla yönetilen bileşenleri ile birlikte COM uygulama tarafından sahip olunan uygulama bildirimi.  
  
2.  Aşağıdaki standart üstbilgi dosyasının başında ekleyin:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Bildirim öğeleri ve onların öznitelikleri hakkında daha fazla bilgi için bkz: [uygulama bildirimleri](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx).  
  
3.  Bildirim sahibi olacak kişileri tanımlayın. Aşağıdaki örnekte, `myComApp` sürüm 1 sahibi bildirim dosyası.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  Bağımlı derlemeleri tanımlayın. Aşağıdaki örnekte, `myComApp` bağlıdır `myManagedComp`.  
  
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
  
5.  Kaydedin ve bildirim dosyasının adı. Yürütülebilir derlemesinin adını .manifest uzantısı tarafından izlenen bir uygulama bildirimi adıdır. Örneğin, uygulama bildirim dosyasının myComApp.exe myComApp.exe.manifest adıdır.  
  
 COM uygulaması ile aynı dizinde bir uygulama bildirimi yükleyebilirsiniz. Alternatif olarak, bunu bir kaynak olarak uygulamanın .exe dosyasına ekleyebilirsiniz. Daha fazla bilgi için ek bilgi için bkz: [yan yana derlemeler hakkında](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx).  
  
#### <a name="to-create-a-component-manifest"></a>Bileşen bildirimi oluşturmak için  
  
1.  Bir XML Düzenleyicisi'ni kullanarak yönetilen derlemeyi tanımlamak için bir bileşen bildirimi oluşturun.  
  
2.  Aşağıdaki standart üstbilgi dosyasının başında ekleyin:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  Dosyanın sahibi tanımlayın. `<assemblyIdentity>` Öğesinin `<dependentAssembly>` uygulama bildirim dosyasının öğesinde bir bileşen bildiriminde eşleşmesi gerekir. Aşağıdaki örnekte, `myManagedComp` sürüm 1.2.3.4 sahibi bildirim dosyası.  
  
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
  
4.  Her sınıf derlemesindeki tanımlayın. Kullanım `<clrClass>` her yönetilen derlemeyi sınıfında benzersiz şekilde tanımlamak için öğesi. Bir alt öğedir öğesi, `<assembly>` öğesi, aşağıdaki tabloda açıklanan özniteliklere sahip.  
  
    |Öznitelik|Açıklama|Gerekli|  
    |---------------|-----------------|--------------|  
    |`clsid`|Etkinleştirilecek sınıfını belirtir tanımlayıcısı.|Evet|  
    |`description`|Kullanıcı bileşeni hakkında bilgilendirir bir dize. Boş bir dize varsayılandır.|Hayır|  
    |`name`|Yönetilen sınıf temsil eden bir dize.|Evet|  
    |`progid`|Geç bağlama etkinleştirmesi için kullanılan tanımlayıcı.|Hayır|  
    |`threadingModel`|COM iş parçacığı modeli. "Both" varsayılan değerdir.|Hayır|  
    |`runtimeVersion`|Ortak dil çalışma zamanı (CLR) sürümün kullanılacağını belirtir. Bu öznitelik belirtmeyin ve CLR zaten yüklü değilse, bileşen CLR sürüm 4 önce en son yüklenen CLR ile yüklenir. V1.0.3705, v1.1.4322 veya v2.0.50727 belirtirseniz, sürümü otomatik olarak ilet son yüklü CLR sürümü CLR sürüm 4 (genellikle v2.0.50727) önce yapar. CLR başka bir sürümü zaten yüklü ve belirtilen sürüm işlemdeki yan yana yüklenebilir, belirtilen sürümü yüklenir; Aksi halde, yüklenen CLR kullanılır. Bu, yükleme hatasına neden olabilir.|Hayır|  
    |`tlbid`|Sınıf türü bilgilerini içeren tür kitaplığı tanımlayıcısı.|Hayır|  
  
     Tüm öznitelik etiketleri büyük/küçük harfe duyarlıdır. OLE/COM ObjectViewer (Oleview.exe) içeren derlemenin verilen tür kitaplığı görüntüleyerek modelleri ve çalışma zamanı sürümü iş parçacığı CLSID, ProgID, elde edebilirsiniz.  
  
     Aşağıdaki bileşeni bildirimini iki sınıf tanımlar `testClass1` ve `testClass2`.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4" />  
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
  
5.  Kaydedin ve bildirim dosyasının adı. Bileşen bildirimi .manifest uzantısı tarafından izlenen derleme kitaplığının adı adıdır. Örneğin, myManagedComp.dll myManagedComp.manifest olur.  
  
 Bir kaynak olarak bileşen bildirimi derlemede katıştırmak gerekir.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Bileşen bildirimi yönetilen bir derlemede katıştırmak için  
  
1.  Aşağıdaki deyim içeren bir kaynak komut dosyası oluşturun:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     Bu bildirimde `myManagedComp.manifest` ekli bileşen bildirimi adıdır. Bu örnekte, komut dosyası dosya adı, `myresource.rc`.  
  
2.  Microsoft Windows Kaynak derleyicisi (Rc.exe) kullanarak komut derleyin. Komut satırında, aşağıdaki komutu yazın:  
  
     `rc myresource.rc`  
  
     RC.exe üreten `myresource.res` kaynak dosyası.  
  
3.  Derlemenin kaynak dosyasını yeniden derleyin ve kaynak dosyasını kullanarak belirtin **/win32res** seçeneği:  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     Yeniden `myresource.res` katıştırılmış kaynağı içeren kaynak dosyasının adıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kayıtsız COM Birlikte Çalışma](../../../docs/framework/interop/registration-free-com-interop.md)  
 [Kayıtsız COM birlikte çalışma için gereksinimleri](http://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da)  
 [COM bileşenlerini kayıtsız etkinleştirme için yapılandırma](http://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe)  
 [Kayıtsız etkinleştirme. NET tabanlı bileşenler: İzlenecek yollar](http://go.microsoft.com/fwlink/?LinkId=158812)
