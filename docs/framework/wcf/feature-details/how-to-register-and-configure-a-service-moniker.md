---
title: 'Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: cd3b6bbb47dfd72bf70091c9ca4d6fc5e228d950
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221551"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma
Yazılı sözleşme ile Windows Communication Foundation (WCF) hizmet bilinen adını COM uygulamasından kullanmadan önce gerekli öznitelik türleri COM ile kaydetme ve COM uygulaması ve ad gerekli bağlama ile yapılandırmanız gerekir yapılandırma.  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>Gerekli öznitelik türleri COM ile kaydetmek için  
  
1.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta veri sözleşmesi WCF hizmetinden almak için aracı. Bir WCF istemcisi derleme ve bir istemci uygulama yapılandırma dosyası için kaynak kodu oluşturur.  
  
2.  Derlemedeki türleri olarak işaretlendiğinden emin olun `ComVisible`. Bunu yapmak için Visual Studio projesinde AssemblyInfo.cs dosyası şu özniteliği ekleyin.  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  Yönetilen WCF istemcisini bir tanımlayıcı adlı bütünleştirilmiş kodu olarak derle. Bu şifreleme anahtar çifti ile imzalama gerektirir. Daha fazla bilgi için [bir derlemeyi tanımlayıcı adla imzalama](https://go.microsoft.com/fwlink/?LinkId=94874) .NET Geliştirici Kılavuzu'nda.  
  
4.  Derleme kaydı (Regasm.exe) aracını `/tlb` seçenek türleri derleme com ile kaydetmek için  
  
5.  Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için Genel Derleme Önbelleği (Gacutil.exe) aracını kullanın.  
  
    > [!NOTE]
    >  Derleme imzalama ve Genel Derleme Önbelleği'ne ekleyerek isteğe bağlı adımlardır ancak bunlar derleme zamanında doğru konumda yükleme işlemini kolaylaştırabilir.  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>COM uygulaması ve ad gerekli bağlama yapılandırması ile yapılandırmak için  
  
-   Bağlama tanımları yerleştirin (tarafından oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturulan istemci uygulama yapılandırma dosyasında) istemci uygulamanın yapılandırma dosyası. Örneğin, bir Visual Basic CallCenterClient.exe adlı 6.0 için yürütülebilir, yapılandırma, yürütülebilir dosya ile aynı dizine içinde CallCenterConfig.exe.config adındaki bir dosyaya yerleştirilmelidir. İstemci uygulaması artık bir ad kullanabilirsiniz. Bağlama yapılandırması bağlama WCF tarafından sağlanan türler standardını birini kullanıyorsanız, gerekli olmadığına dikkat edin.  
  
     Şu tür kaydedilir.  
  
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
  
     Uygulama kullanılarak açılır bir `wsHttpBinding` bağlama. Aşağıdaki örnek ad dizeleri, belirtilen tür ve uygulama yapılandırması için kullanılır.  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     Bu ad dizeleri içeren derlemeyi bir başvuru ekledikten sonra bir Visual Basic 6.0 uygulamadaki kullanabilirsiniz `IMathService` türleri, aşağıdaki örnek kodda gösterildiği gibi.  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     Bu örnekte, bağlama yapılandırması için tanım `Binding1` vb6appname.exe.config gibi istemci uygulaması için uygun şekilde adlandırılmış yapılandırma dosyasında depolanır.  
  
    > [!NOTE]
    >  C#, C++ veya başka bir .NET dil uygulama benzer kodu kullanabilirsiniz.  
  
    > [!NOTE]
    >  : Bilinen adı yanlış biçimlendirilmiş veya hizmet kullanılamıyor durumunda çağrısı `GetObject` "Söz dizimi geçersiz" hatası döndürür. Bu hata iletisini alırsanız kullandığınız ad doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
     Bu konu hizmet bilinen adı VB 6.0 koddan kullanmaya odaklanmıştır olsa da, diğer dillerdeki hizmet bilinen adı kullanabilirsiniz. C++ içinden bir takma ad'ı kullanarak kod olduğunda oluşturulan Svcutil.exe derleme aşağıdaki kodda gösterildiği gibi "ile no_namespace named_guids raw_interfaces_only" aktarılmalıdır.  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     Tüm yöntemler döndürür, bu içeri aktarılan Arabirim tanımları değiştirir bir `HResult`. Herhangi bir dönüş değeri, out parametreleri içine dönüştürülür. Genel yöntemler yürütülmesini aynı kalır. Bu proxy üzerinde bir yöntemi çağırırken özel durumun nedenini belirlemenize olanak sağlar. Bu işlev, yalnızca C++ kodundan kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
