---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: hizmet bilinen adını kaydetme ve yapılandırma'
title: 'Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 9c6867941a5b96c6ced0f8e371e10697144bd121
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643468"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma

Türü belirlenmiş bir sözleşmeyle bir COM uygulaması içinde Windows Communication Foundation (WCF) hizmet bilinen adını kullanmadan önce, gerekli olan türleri COM 'a kaydetmeniz ve COM uygulamasını ve bilinen adı gerekli bağlama yapılandırması ile yapılandırmanız gerekir.

## <a name="register-the-required-attributed-types-with-com"></a>Gerekli öznitelikli türleri COM 'a kaydetme

1. WCF hizmetinden meta veri sözleşmesini almak için [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) aracını kullanın. Bu, bir WCF istemci derlemesi ve bir istemci uygulama yapılandırma dosyası için kaynak kodu oluşturur.

2. Derlemedeki türlerin olarak işaretlendiğinden emin olun `ComVisible` . Bunu yapmak için, Visual Studio projenizdeki *AssemblyInfo.cs* dosyasına aşağıdaki özniteliği ekleyin.

    ```csharp
    [assembly: ComVisible(true)]
    ```

3. Yönetilen WCF istemcisini tanımlayıcı adlı bir derleme olarak derleyin. Bu, bir şifreleme anahtar çiftiyle imza gerektirir. Daha fazla bilgi için bkz. [bir derlemeyi güçlü bir adla imzalama](../../../standard/assembly/sign-strong-name.md).

4. Derlemeyi `-tlb` com ile derlemeye kaydetme seçeneğiyle birlikte derleme kaydı (Regasm.exe) aracını kullanın.

5. Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için genel bütünleştirilmiş kod önbelleği (Gacutil.exe) aracını kullanın.

    > [!NOTE]
    > Derlemeyi imzalama ve genel bütünleştirilmiş kod önbelleğine ekleme isteğe bağlı adımlardır, ancak çalışma zamanında derlemeyi doğru konumdan yükleme işlemini basitleştirebilir.

## <a name="configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>COM uygulamasını ve bilinen adı gerekli bağlama yapılandırmasıyla yapılandırın

- İstemci uygulamasının yapılandırma dosyasındaki bağlama tanımlarını (oluşturulan istemci uygulama yapılandırma dosyasında bulunan [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan) yerleştirin. Örneğin, CallCenterClient.exe adlı bir Visual Basic 6,0 yürütülebilir dosyası için yapılandırma, yürütülebilir dosya ile aynı dizin içinde CallCenterConfig.exe.config adlı bir dosyaya yerleştirilmelidir. İstemci uygulaması artık bilinen adı kullanabilir. WCF tarafından sunulan standart bağlama türlerinden birini kullanıyorsanız bağlama yapılandırmasının gerekli olmadığını unutmayın.

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

     Uygulama, bağlama kullanılarak gösterilir `wsHttpBinding` . Verilen tür ve uygulama yapılandırması için aşağıdaki örnek bilinen ad dizeleri kullanılır.

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1
    ```

     veya

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}
    ```

     Aşağıdaki örnek kodda gösterildiği gibi, türleri içeren derlemeye bir başvuru ekledikten sonra, bir Visual Basic 6,0 uygulaması içinden bu bilinen ad dizelerinin birini kullanabilirsiniz `IMathService` .

    ```vb
    Dim mathProxy As IMathService
    Dim result As Integer

    Set mathProxy = GetObject( _
            "service4:address=http://localhost/MathService, _
            binding=wsHttpBinding, _
            bindingConfiguration=Binding1")

    result = mathProxy.Add(3, 5)
    ```

     Bu örnekte, bağlama yapılandırması tanımı, `Binding1` istemci uygulaması için *vb6appname.exe.config* gibi bir uygun şekilde adlı yapılandırma dosyasında depolanır.

    > [!NOTE]
    > Benzer kodu C#, C++ veya diğer herhangi bir .NET dil uygulamasında kullanabilirsiniz.

    > [!NOTE]
    > Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" hatası döndürür. Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.

     Bu konu, Visual Basic 6,0 kodundan hizmet bilinen adını kullanmaya odaklansa da, diğer dillerden bir hizmet bilinen adı kullanabilirsiniz. C++ kodundan bilinen bir ad kullanırken, Svcutil.exe oluşturulan derleme aşağıdaki kodda gösterildiği gibi "no_namespace named_guids raw_interfaces_only" ile içeri aktarılmalıdır.

    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids
    ```

     Bu, içeri aktarılan arabirim tanımlarını tüm yöntemlerin bir döndürmesini sağlayacak şekilde değiştirir `HResult` . Diğer tüm dönüş değerleri Out parametrelerine dönüştürülür. Yöntemlerin genel yürütülmesi aynı kalır. Bu, proxy üzerinde bir yöntemi çağırırken bir özel durumun nedenini belirlemenizi sağlar. Bu işlevsellik yalnızca C++ kodundan kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
