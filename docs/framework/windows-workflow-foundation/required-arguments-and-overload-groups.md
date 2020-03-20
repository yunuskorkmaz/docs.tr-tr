---
title: Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 4eb62306f52b8ff890d5a5333c3789bd84ad7f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142946"
---
# <a name="required-arguments-and-overload-groups"></a>Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar
Etkinlikler, belirli bağımsız değişkenlerin yürütme için geçerli olması için belirli bağımsız değişkenlerin bağlanması için yapılandırılabilir. Öznitelik, `RequiredArgument` bir etkinlikteki belirli bağımsız değişkenlerin gerekli `OverloadGroup` olduğunu ve öznitelik in gerekli bağımsız değişkenkategorilerini birlikte gruplandırmak için kullanılır. İşleçlik leri kullanarak, etkinlik yazarları basit veya karmaşık etkinlik doğrulama yapılandırmaları sağlayabilir.  
  
## <a name="using-required-arguments"></a>Gerekli Bağımsız Değişkenleri Kullanma  
 Bir etkinlikte `RequiredArgument` öznitelik kullanmak için, kullanarak <xref:System.Activities.RequiredArgumentAttribute>istenen bağımsız değişkenleri gösterir. Bu örnekte, `Add` iki gerekli bağımsız değişkeni olan bir etkinlik tanımlanır.  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 XAML'de gerekli bağımsız değişkenler <xref:System.Activities.RequiredArgumentAttribute>de kullanılarak belirtilir. Bu örnekte `Add` etkinlik üç bağımsız değişken kullanılarak <xref:System.Activities.Statements.Assign%601> tanımlanır ve ekleme işlemini gerçekleştirmek için bir etkinlik kullanır.  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 Etkinlik kullanılırsa ve gerekli bağımsız değişkenlerden biri bağlı değilse aşağıdaki doğrulama hatası döndürülür.  
  
 **Gerekli bir etkinlik bağımsız değişkeni 'Operand1' için değer verilmedi.**  
> [!NOTE]
> Doğrulama hatalarını ve uyarılarını denetleme ve işleme hakkında daha fazla bilgi için [bkz.](invoking-activity-validation.md)  
  
## <a name="using-overload-groups"></a>Aşırı Yük Gruplarını Kullanma

Aşırı yükleme grupları, bir etkinlikte hangi bağımsız değişken birleşimlerinin geçerli olduğunu belirtmek için bir yöntem sağlar. Bağımsız değişkenler kullanılarak <xref:System.Activities.OverloadGroupAttribute>birlikte gruplandırılır. Her gruba <xref:System.Activities.OverloadGroupAttribute>. Etkinlik, aşırı yükleme grubundaki yalnızca bir bağımsız değişken kümesi bağlı olduğunda geçerlidir. Aşağıdaki örnekte, `CreateLocation` bir sınıf tanımlanır.  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }
}  
```  
  
 Bu etkinliğin amacı, ABD'de bir konum belirtmektir. Bunu yapmak için, etkinliğin kullanıcı bağımsız değişkenler üç grup birini kullanarak konumu belirtebilirsiniz. Bağımsız değişkenlerin geçerli birleşimlerini belirtmek için üç aşırı yükleme grubu tanımlanır. `G1``Latitude` ve `Longitude` bağımsız değişkenleri içerir. `G2`içerir `Street` `City`, `State`ve . `G3`içerir `Street` `Zip`ve . `Name`ayrıca gerekli bir bağımsız değişkendir, ancak aşırı yükleme grubunun bir parçası değildir. Bu etkinliğin geçerli olabilmek için, `Name` bir ve yalnızca bir aşırı yükleme grubundaki tüm bağımsız değişkenlerle birbirine bağlı olması gerekir.  
  
 [Veritabanı Erişim Etkinlikleri](./samples/database-access-activities.md) örneğinden alınan aşağıdaki örnekte, iki aşırı `ConnectionString` `ConfigFileSectionName`yükleme grubu vardır: ve . Bu etkinliğin geçerli olabilmesi `ProviderName` için, `ConnectionString` bağımsız değişkenler `ConfigName` veya bağımsız değişkenin bağlı olması gerekir, ancak her ikisi de geçerli değildir.  
  
```csharp  
public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }
}  
```  
  
 Aşırı yükleme grubu tanımlanırken:  
  
- Aşırı yükleme grubu bir alt küme veya başka bir aşırı yük grubunun eşdeğer kümesi olamaz.  
  
    > [!NOTE]
    > Bu kuralın bir istisnası vardır. Aşırı yük grubu başka bir aşırı yük grubunun alt kümesiyse ve `RequiredArgument` alt `false`küme yalnızca aşırı yükleme grubunun geçerli olduğu bağımsız değişkenleri içeriyorsa.  
  
- Aşırı yük grupları çakışabilir, ancak grupların kesişimi aşırı yük gruplarından birinin veya her ikisinin gerekli tüm bağımsız değişkenlerini içeriyorsa bir hatadır. Önceki örnekte `G2` ve `G3` aşırı yükleme grupları çakıştı, ancak kesişim bir veya her iki grubun tüm bağımsız değişkenlerini içermediğinden bu geçerliydi.  
  
 Bir aşırı yük grubunda bağımsız değişkenler bağlanırken:  
  
- Gruptaki tüm `RequiredArgument` bağımsız değişkenler bağlıysa, aşırı yükleme grubu bağlı olarak kabul edilir.  
  
- Bir grubun sıfır `RequiredArgument` bağımsız değişkeni varsa ve en az bir bağımsız değişken bağlıysa, grup bağlı olarak kabul edilir.  
  
- Bir aşırı yük grubunda bağımsız değişken yoksa, `RequiredArgument` aşırı yük grupları bağlı değilse, bir doğrulama hatasıdır.  
  
- Birden fazla aşırı yük grubuna bağlı olması bir hatadır, yani bir aşırı yük grubundaki tüm gerekli bağımsız değişkenler bağlanır ve başka bir aşırı yükleme grubundaki herhangi bir bağımsız değişken de bağlıdır.
