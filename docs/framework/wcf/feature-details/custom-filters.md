---
title: Özel Filtreler
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 4140a944ed195e1defc1a0677d8e26ff4ff85beb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489761"
---
# <a name="custom-filters"></a>Özel Filtreler
Özel Filtreler, sistem tarafından sağlanan ileti filtreleri kullanılarak elde edemiyor eşleşen mantığı tanımlamanıza olanak sağlar. Örneğin, belirli ileti öğesi karma hale getirir ve filtre doğru döndürme zorunluluğu olup olmadığını belirlemek için değeri inceler özel filtre veya yanlış oluşturabilirsiniz.  
  
## <a name="implementation"></a>Uygulama  
 Özel filtre uygulamasıdır <xref:System.ServiceModel.Dispatcher.MessageFilter> soyut taban sınıfı. Özel filtre uygularken Oluşturucusu isteğe bağlı olarak tek bir dize parametresi kabul edebilir. Bu parametre, herhangi bir değer veya filtre gerçekleştirmek için çalışma zamanında gereken yapılandırma eşleşen sağlamak amacıyla MessageFilter oluşturucuya geçirilen yapılandırma bilgilerini içerir. Örneğin, bu iletinin değerlendirilen içinde filtre arar bir değer sağlamak için kullanılabilir. Aşağıdaki örnek, bir dize parametre kabul eden bir özel ileti filtresi temel uyarlamasını gösterir:  
  
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
>  Gerçek bir uygulama, bu ileti filtresi döndürmelidir belirlemek için ileti inceleyeceksiniz mantığı eşleşme yöntemleri içeren **true** veya **false**.  
  
### <a name="performance"></a>Performans  
 Özel filtre uygularken, filtre bir ileti değerlendirmesini tamamlamak gereken en fazla süreyi dikkate önemlidir. Bir eşleşme önce bir ileti birden çok filtreleriyle hesaplanan, tüm filtreleri değerlendirilmeden önce istemci isteği zaman aşımına yaptığından emin olmak önemlidir. Bu nedenle bir özel filtre yalnızca içeriği veya filtre ölçütünü eşleşip eşleşmediğini belirlemek için bir ileti özniteliklerini değerlendirmek için gereken kodu içermelidir.  
  
 Genel olarak, aşağıdaki özel filtre uygularken kaçınmanız gerekir:  
  
-   GÇ, verileri diske veya bir veritabanına kaydetme gibi.  
  
-   İşlem, bir belge içinde birden çok kayıt üzerinden döngü gibi gereksizdir.  
  
-   Paylaşılan kaynaklar üzerinde bir kilit elde etme veya bir veritabanında aramalar gerçekleştiren çağrıları gibi işlemleri engelliyor.  
  
 Özel filtre bir üretim ortamında kullanmadan önce Filtre bir ileti değerlendirmek için geçen ortalama süreyi belirlemek için performans testlerini çalıştırmanız gerekir. Filtre tablosunda kullanılan diğer filtrelerle Ortalama işleme süresi ile birlikte kullanıldığında, bu doğru şekilde istemci uygulaması tarafından belirtilen en büyük zaman aşımı değeri belirlemenize olanak tanır.  
  
## <a name="usage"></a>Kullanım  
 Özel filtre yönlendirme hizmeti ile kullanabilmeniz için onu filtre tabloya yeni bir filtre giriş türü belirterek "Özel," İleti Filtresi tam olarak nitelenmiş tür adını ve derlemenizi adını eklemeniz gerekir.  Diğer bir MessageFilters olduğu gibi ile özel filtrenin oluşturucuya geçirilen dize filterData belirtebilirsiniz.  
  
 Aşağıdaki örnekler, yönlendirme hizmeti ile özel bir filtre kullanarak göstermektedir:  
  
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
