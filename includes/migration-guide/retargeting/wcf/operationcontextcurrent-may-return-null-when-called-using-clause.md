---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614751"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext. Current, using yan tümcesinde çağrıldığında null döndürebilir

#### <a name="details"></a>Ayrıntılar

<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>`null` <xref:System.NullReferenceException> aşağıdaki koşulların tümü doğruysa dönebilir ve bir sonuç verebilir:

- Özelliğinin değerini, <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> veya döndüren bir yöntemde alırsınız <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .
- <xref:System.ServiceModel.OperationContextScope>Bir `using` yan tümcede nesneyi örnekleyebilirsiniz.
- İçindeki özelliğinin değerini elde edersiniz <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> `using statement` . Örneğin:

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a>Öneri

Bu sorunu gidermek için aşağıdakileri yapabilirsiniz:

- Yeni bir nesne olmayan yeni bir nesne örneği oluşturmak için kodunuzu aşağıdaki şekilde değiştirin `null` <xref:System.ServiceModel.OperationContext.Current%2A> :

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- En son güncelleştirmeyi .NET Framework 4.6.2 veya .NET Framework daha sonraki bir sürüme yükseltin. Bu, içindeki akışını devre dışı <xref:System.Threading.ExecutionContext> bırakır <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> ve .NET Framework 4.6.1 ve ÖNCEKI sürümlerde WCF uygulamalarının davranışını geri yükler. Bu davranış yapılandırılabilir; yapılandırma dosyanıza aşağıdaki uygulama ayarı eklenerek eşdeğerdir:

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    Bu değişiklik istenene ve uygulamanız, işlem bağlamları arasındaki yürütme bağlamına bağımlıysa, akışını şu şekilde etkinleştirebilirsiniz:

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
