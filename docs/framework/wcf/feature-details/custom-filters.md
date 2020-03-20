---
title: Özel Filtreler
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ae020173544372c3ce097c8ac57e53f3fde37514
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185204"
---
# <a name="custom-filters"></a>Özel Filtreler
Özel filtreler, sistem tarafından sağlanan ileti filtreleri kullanılarak gerçekleştirilemeyen eşleşen mantığı tanımlamanıza olanak sağlar. Örneğin, belirli bir ileti öğesini eleman olarak eleman olarak eleman olarak eleman olarak eleman olarak eleman olarak döndürecek ve filtrenin doğru mu yoksa yanlış mı döndüreceğini belirlemek için değeri inceleyen özel bir filtre oluşturabilirsiniz.  
  
## <a name="implementation"></a>Uygulama  
 Özel bir filtre soyut <xref:System.ServiceModel.Dispatcher.MessageFilter> taban sınıfının bir uygulamasıdır. Özel filtrenizi uygularken, oluşturucu isteğe bağlı olarak tek bir dize parametresini kabul edebilir. Bu parametre, filtrenin eşleşmeleri gerçekleştirmek için çalışma zamanında ihtiyaç duyduğu değerleri veya yapılandırmayı sağlamak için MessageFilter oluşturucusuna aktarılan yapılandırma bilgilerini içerir. Örneğin, bu, filtrenin değerlendirilmekte olan ileti içinde aradığı bir değeri sağlamak için kullanılabilir. Aşağıdaki örnek, dize parametresi kabul eden özel bir ileti filtresinin temel uygulamasını gösterir:  
  
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
> Gerçek bir uygulamada, Eşleme yöntemi(ler) bu ileti filtresinin **doğru** mu yoksa **yanlış**mı döndüreceğini belirlemek için iletiyi inceleyecek mantık içerir.  
  
### <a name="performance"></a>Performans  
 Özel bir filtre uygularken, filtrenin iletinin değerlendirmesini tamamlaması için gereken maksimum süreyi göz önünde bulundurmak önemlidir. Bir ileti eşleşme bulunmadan önce birden çok filtreye karşı değerlendirilebileceğinden, tüm filtreler değerlendirilmeden önce istemci isteğinin zaman ödemediğinden emin olmak önemlidir. Bu nedenle, özel bir filtre, filtre ölçütlerine uygun olup olmadığını belirlemek için iletinin içeriğini veya özniteliklerini değerlendirmek için yalnızca gerekli kodu içermelidir.  
  
 Genel olarak, özel bir filtre uygularken aşağıdakilerden kaçınmalısınız:  
  
- IO, diske veya veritabanına veri kaydetme gibi.  
  
- Bir belgedeki birden çok kaydın üzerinden döngü gibi gereksiz işleme.  
  
- Paylaşılan kaynaklarda kilit alma veya veritabanına karşı arama lar gerçekleştirme gibi işlemleri engelleme.  
  
 Üretim ortamında özel bir filtre kullanmadan önce, filtrenin bir iletiyi değerlendirmek için gereken ortalama süreyi belirlemek için performans testleri çalıştırmanız gerekir. Filtre tablosunda kullanılan diğer filtrelerin ortalama işlem süresiyle birleştirildiğinde, bu, istemci uygulaması tarafından belirtilmesi gereken maksimum zaman aşım değerini doğru bir şekilde belirlemenize olanak sağlar.  
  
## <a name="usage"></a>Kullanım  
 Yönlendirme Hizmeti ile özel filtrenizi kullanmak için, "Özel" türünde yeni bir filtre girişi, ileti filtresinin tam nitelikli tür adı ve derlemenizin adını belirterek filtre tablosuna eklemeniz gerekir.  Diğer MessageFilters'larda olduğu gibi, özel filtrenizin oluşturucusuna aktaredilecek dize filtresiVerileri belirtebilirsiniz.  
  
 Aşağıdaki örnekler, Yönlendirme Hizmeti ile özel bir filtre kullanarak gösterilmektedir:  
  
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
