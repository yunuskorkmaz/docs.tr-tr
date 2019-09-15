---
title: 'Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 547e507b4a1115de81532263c34964cd20f15d4e
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972140"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma
Türü belirlenmiş bir sözleşmeyle bir COM uygulaması içinde Windows Communication Foundation (WCF) hizmet bilinen adını kullanmadan önce, gerekli öznitelikli türleri COM 'a kaydetmeniz ve COM uygulamasını ve bilinen bağlamayı gerekli bağlamaya göre yapılandırmanız gerekir yapılandırmada.  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>Gerekli türleri COM 'a kaydetmek için  
  
1. WCF hizmetinden meta veri sözleşmesini almak için [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracını kullanın. Bu, bir WCF istemci derlemesi ve bir istemci uygulama yapılandırma dosyası için kaynak kodu oluşturur.  
  
2. Derlemedeki türlerin olarak `ComVisible`işaretlendiğinden emin olun. Bunu yapmak için, Visual Studio projenizdeki AssemblyInfo.cs dosyasına aşağıdaki özniteliği ekleyin.  
  
    ```csharp
    [assembly: ComVisible(true)]  
    ```  
  
3. Yönetilen WCF istemcisini tanımlayıcı adlı bir derleme olarak derleyin. Bu, bir şifreleme anahtar çiftiyle imza gerektirir. Daha fazla bilgi için bkz. .NET geliştirici kılavuzunda [güçlü bir ada sahip bir derlemeyi imzalama](https://go.microsoft.com/fwlink/?LinkId=94874) .  
  
4. Derlemeyi com ile derlemeye kaydetme `/tlb` seçeneğiyle birlikte derleme kaydı (Regasm. exe) aracını kullanın.  
  
5. Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için genel bütünleştirilmiş kod önbelleği (Gacutil. exe) aracını kullanın.  
  
    > [!NOTE]
    > Derlemeyi imzalama ve genel bütünleştirilmiş kod önbelleğine ekleme isteğe bağlı adımlardır, ancak çalışma zamanında derlemeyi doğru konumdan yükleme işlemini basitleştirebilir.  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>COM uygulamasını ve bilinen bağlamayı gereken bağlama yapılandırması ile yapılandırmak için  
  
- İstemci uygulamasının yapılandırma dosyasındaki bağlama tanımlarını (oluşturulan istemci uygulama yapılandırma dosyasında bulunan [ServiceModel meta veri yardımcı programı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan) yerleştirin. Örneğin, CallCenterClient. exe adlı bir Visual Basic 6,0 yürütülebilir dosyası için yapılandırma, yürütülebilir dosya ile aynı dizin içinde CallCenterConfig. exe. config adlı bir dosyaya yerleştirilmelidir. İstemci uygulaması artık bilinen adı kullanabilir. WCF tarafından sunulan standart bağlama türlerinden birini kullanıyorsanız bağlama yapılandırmasının gerekli olmadığını unutmayın.  
  
     Aşağıdaki tür kaydedilir.  
  
    ```csharp  
    using System.ServiceModel;  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     Uygulama, `wsHttpBinding` bağlama kullanılarak gösterilir. Verilen tür ve uygulama yapılandırması için aşağıdaki örnek bilinen ad dizeleri kullanılır.  
  
    ``` 
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ``` 
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     Aşağıdaki örnek kodda gösterildiği gibi, `IMathService` türleri içeren derlemeye bir başvuru ekledikten sonra, bir Visual Basic 6,0 uygulaması içinden bu bilinen ad dizelerinin birini kullanabilirsiniz.  
  
    ```vb  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     Bu örnekte, bağlama yapılandırması `Binding1` tanımı, istemci uygulaması için vb6appname. exe. config gibi bir uygun şekilde adlı yapılandırma dosyasında depolanır.  
  
    > [!NOTE]
    > Benzer bir kodu, C# C++bir, veya başka bir .NET dil uygulamasında kullanabilirsiniz.  
  
    > [!NOTE]
    > : Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" hatası döndürür. Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
     Bu konu, VB 6,0 kodundaki hizmet bilinen adını kullanmaya odaklansa da diğer dillerden bir hizmet bilinen adı kullanabilirsiniz. Koddan bilinen bir ad kullanırken C++ , Svcutil. exe tarafından oluşturulan derleme aşağıdaki kodda gösterildiği gibi "no_namespace named_guids raw_interfaces_only" ile içeri aktarılmalıdır.  
  
    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     Bu, içeri aktarılan arabirim tanımlarını tüm yöntemlerin bir `HResult`döndürmesini sağlayacak şekilde değiştirir. Diğer tüm dönüş değerleri Out parametrelerine dönüştürülür. Yöntemlerin genel yürütülmesi aynı kalır. Bu, proxy üzerinde bir yöntemi çağırırken bir özel durumun nedenini belirlemenizi sağlar. Bu işlevsellik yalnızca C++ koddan kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
