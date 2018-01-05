---
title: "Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e5c57927a455b5d2a253becac35b1bf9033933f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma
Kullanmadan önce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet bilinen adı yazılı sözleşme ile COM uygulama içinde gerekli öznitelikli türleri COM ile kaydetme ve COM uygulama ve ad gerekli bağlama yapılandırması ile yapılandırmanız gerekir.  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>Gerekli öznitelikli türleri COM ile kaydetmek için  
  
1.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta verileri sözleşmeden almak için aracı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet. Bu kaynak kodunu oluşturur bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci derleme ve bir istemci uygulama yapılandırma dosyası.  
  
2.  Derlemedeki türleri olarak işaretlenmediğinden emin olun `ComVisible`. Bunu yapmak için Visual Studio projenizi AssemblyInfo.cs dosyasında şu özniteliği ekleyin.  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  Yönetilen derleme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci tanımlayıcı adlı bir derleme olarak. Bu, bir şifreleme anahtar çifti ile imzalama gerektirir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Bir derlemeyi tanımlayıcı adla imzalama](http://go.microsoft.com/fwlink/?LinkId=94874) .NET Geliştirici Kılavuzu.  
  
4.  Derleme kaydı (Regasm.exe) aracıyla kullanın `/tlb` türleri com derlemesine kaydetmek için seçeneği  
  
5.  Derleme genel derleme önbelleğine eklemek için Genel Derleme Önbelleği (Gacutil.exe) aracını kullanın.  
  
    > [!NOTE]
    >  Derleme imzalama ve genel derleme önbelleğine ekleme isteğe bağlı adımlardır, ancak çalışma zamanında doğru konumdan derlemesi yüklenirken işlemini kolaylaştırabilir.  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>COM uygulama ve ad ile gerekli bağlama yapılandırması yapılandırmak için  
  
-   Bağlama tanımları yerleştirin (tarafından oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturulan istemci uygulama yapılandırma dosyasında) istemci uygulamanın yapılandırma dosyasında. Örneğin, bir Visual Basic CallCenterClient.exe adlı 6.0 için yürütülebilir, yapılandırma, yürütülebilir dosya ile aynı dizinde içinde CallCenterConfig.exe.config adlı bir dosyaya yerleştirilmelidir. İstemci uygulaması artık bilinen ad olarak kullanabilirsiniz. Bağlama yapılandırması tarafından sağlanan türleri bağlama standart birini kullanarak gerekli değilse Not [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
     Aşağıdaki türü kaydedilir.  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     Uygulama kullanılarak kullanıma sunulan bir `wsHttpBinding` bağlama. Belirtilen tür ve uygulama yapılandırması için aşağıdaki örnek ad dizeleri kullanılır.  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     Bir başvuru içeren derlemenin ekledikten sonra ek olarak, Visual Basic 6.0 uygulama içinde bu ad dizelerden herhangi biri kullanabilirsiniz `IMathService` türleri, aşağıdaki örnek kodda gösterildiği gibi.  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     Bu örnekte, bağlama yapılandırması tanımı `Binding1` vb6appname.exe.config gibi istemci uygulaması için uygun adlandırılmış yapılandırma dosyasında depolanır.  
  
    > [!NOTE]
    >  C#, C++ veya başka bir .NET dil uygulama benzer bir kod kullanabilirsiniz.  
  
    > [!NOTE]
    >  : Ad hatalı biçimlendirilmiş olması veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi" hatası döndürür. Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.  
  
     Bu konuda VB 6.0 kodundan hizmet bilinen adı kullanma odaklanıyor olsa da, diğer dillerdeki hizmet bilinen adı kullanabilirsiniz. C++ içinden bir ad kullanarak kod yazarken oluşturulan Svcutil.exe derleme aşağıdaki kodda gösterildiği gibi "ile no_namespace named_guids raw_interfaces_only" aktarılmalıdır.  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     Böylece tüm yöntemleri döndürür bu alınan Arabirim tanımları değiştiren bir `HResult`. Diğer tüm dönüş değerleri out Parametreleri uygulamasına dönüştürülür. Genel yöntemler yürütülmesi aynı kalır. Bu yöntem proxy çağırırken özel bir durum nedenini belirlemenize olanak sağlar. Bu işlevsellik yalnızca C++ koddan kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
