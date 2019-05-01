---
title: Özel Filtreler
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 4140a944ed195e1defc1a0677d8e26ff4ff85beb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857226"
---
# <a name="custom-filters"></a>Özel Filtreler
Özel Filtreler sistem tarafından sağlanan ileti filtreleri kullanarak elde edemiyor eşleşen mantığı tanımlamanızı sağlar. Örneğin, bir özel ileti öğesi karma hale getirir ve ardından filtrenin doğru döndürme zorunluluğu olup olmadığını belirlemek için değer inceler özel filtre ya da yanlış oluşturabilirsiniz.  
  
## <a name="implementation"></a>Uygulama  
 Özel bir filtre uygulamasıdır <xref:System.ServiceModel.Dispatcher.MessageFilter> soyut temel sınıf. Özel filtrenizle uygularken Oluşturucusu isteğe bağlı olarak tek bir dize parametresi kabul edebilir. Bu parametre, herhangi bir değer veya filtre gerçekleştirmek için çalışma zamanında gereken yapılandırma eşleşen sağlamak amacıyla MessageFilter oluşturucuya geçirilen yapılandırma bilgilerini içerir. Örneğin, bu filtre değerlendirilen ileti içinde arar bir değer sağlamak için kullanılabilir. Aşağıdaki örnek, bir dize parametresi kabul eden bir özel ileti filtresi uygulaması gösterir:  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
>  Gerçek bir uygulamada eşleştirme yöntemleri bu ileti filtresi döndürmelidir belirlemek için ileti inceleyeceği mantığı içeren **true** veya **false**.  
  
### <a name="performance"></a>Performans  
 Özel filtre uygulanırken, filtre bir ileti değerlendirmesini tamamlamak gereken süre uzunluğu en fazla dikkate önemlidir. Önce bir eşleşme bulunduğu bir ileti birden çok filtrelere göre değerlendirilebilir beri tüm filtreleri değerlendirilmeden önce istemci isteğinin zaman aşımına uğramaz sağlamak önemlidir. Bu nedenle özel filtre yalnızca içeriğini veya özniteliklerini filtre ölçütlerini eşleşip eşleşmediğini belirlemek için bir ileti değerlendirmek için gereken kodu içermesi gerekir.  
  
 Genel olarak, aşağıdaki özel filtre uygularken kaçınmanız gerekir:  
  
- GÇ, verileri diske veya bir veritabanına kaydetme gibi.  
  
- İşlem, bir belge içinde birden çok kayıt üzerinde döngü gibi gereksiz.  
  
- Paylaşılan kaynaklar üzerinde bir kilit alma veya bir veritabanında aramalar gerçekleştiren çağrıları gibi işlemleri engelliyor.  
  
 Özel filtre bir üretim ortamında kullanmadan önce Filtre bir ileti değerlendirmek için gereken ortalama süreyi belirlemek için performans testleri çalıştırmanız gerekir. Ortalama işlem süresi filtre tablosunda kullanılan bir filtre ile birlikte kullanıldığında, bu istemci uygulaması tarafından belirtilen en uzun zaman aşımı değeri doğru bir şekilde belirlemenize olanak tanır.  
  
## <a name="usage"></a>Kullanım  
 Özel filtrenizle yönlendirme hizmeti ile kullanmak için filtre tabloya yeni bir filtre giriş türü belirterek "Özel," İleti Filtresi tam olarak nitelenmiş tür adını ve derlemenizin adını eklemeniz gerekir.  İle diğer MessageFilters olduğu gibi özel filtrenin oluşturucuya geçirilen dize filterData belirtebilirsiniz.  
  
 Aşağıdaki örnekler yönlendirme hizmeti ile özel bir filtre kullanarak göstermektedir:  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"   
            customType="CustomAssembly.MyMessageFilter,   
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
