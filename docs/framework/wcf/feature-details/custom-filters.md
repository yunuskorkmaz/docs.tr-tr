---
title: Özel Filtreler
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ade387524c9ca6c8ef337ccf6a5b3453b7df976b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945374"
---
# <a name="custom-filters"></a>Özel Filtreler
Özel filtreler, sistem tarafından sağlanmış ileti filtreleri kullanılarak gerçekleştiresağlanmayan eşleşen mantığı tanımlamanızı sağlar. Örneğin, belirli bir ileti öğesini karma hale getirmek için bir özel filtre oluşturabilir ve sonra filtrenin true veya false olarak döndürülüp döndürülmeyeceğini tespit etmek için değeri incelemeniz gerekebilir.  
  
## <a name="implementation"></a>Uygulama  
 Özel filtre <xref:System.ServiceModel.Dispatcher.MessageFilter> soyut temel sınıfın bir uygulamasıdır. Özel filtrenizi uygularken, Oluşturucu isteğe bağlı olarak tek bir dize parametresini kabul edebilir. Bu parametre, filtre uygulamak için filtrenin çalışma zamanında ihtiyacı olan herhangi bir değer veya yapılandırma sağlamak üzere MessageFilter oluşturucusuna geçirilen yapılandırma bilgilerini içerir. Örneğin, bu, filtrenin değerlendirilen ileti içinde aradığı bir değer sağlamak için kullanılabilir. Aşağıdaki örnek, bir dize parametresini kabul eden özel bir ileti filtresinin temel bir uygulamasını göstermektedir:  
  
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
> Gerçek bir uygulamada, eşleşme yöntemi (ler), bu ileti filtresinin **true** veya **false**döndürmesi gerekip gerekmediğini belirleyecek şekilde iletiyi inceleyecek mantığı içerir.  
  
### <a name="performance"></a>Performans  
 Özel bir filtre uygularken, filtrenin bir ileti değerlendirmesini tamamlaması için gereken en uzun süreyi dikkate almanız önemlidir. Bir ileti bir eşleşme bulunamadığı için birden çok filtreye karşı değerlendirilebileceğinizden, tüm filtreler hesaplanmadan önce istemci isteğinin zaman aşımına memesini sağlamak önemlidir. Bu nedenle, özel bir filtrenin filtre ölçütleriyle eşleşip eşleşmediğini anlamak için yalnızca bir iletinin içeriğini veya özniteliklerini değerlendirmek için gereken kodu içermesi gerekir.  
  
 Genel olarak, bir özel filtre uygularken aşağıdakilerden kaçınmanız gerekir:  
  
- Verileri diske veya bir veritabanına kaydetme gibi GÇ.  
  
- Belgedeki birden çok kayıt üzerinde döngü gibi gereksiz işleme.  
  
- Paylaşılan kaynaklar üzerinde bir kilit elde etmek veya bir veritabanında arama gerçekleştirmek için gereken çağrılar gibi engelleyici işlemler.  
  
 Bir üretim ortamında özel bir filtre kullanmadan önce, filtrenin bir iletiyi değerlendirmek için aldığı ortalama süreyi öğrenmek için performans testlerini çalıştırmalısınız. Filtre tablosunda kullanılan diğer filtrelerin ortalama işlem süresi ile birleştirildiğinde, bu, istemci uygulaması tarafından belirtilmesi gereken en büyük zaman aşımı değerini doğru bir şekilde belirlemenizi sağlar.  
  
## <a name="usage"></a>Kullanım  
 Özel filtrenizi yönlendirme hizmetiyle kullanabilmeniz için, "Custom" türünde yeni bir filtre girişi belirterek filtre tablosuna eklemeniz gerekir, ileti filtresinin tam tür adı ve derlemenizin adı.  Diğer MessageFilters gibi, özel filtreniz yapıcısına geçirilecek olan filterData dizesini de belirtebilirsiniz.  
  
 Aşağıdaki örneklerde, yönlendirme hizmeti ile özel bir filtrenin kullanılması gösterilmektedir:  
  
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
