---
title: Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 84384e90be0036036477d9b4249832f544e17d08
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989303"
---
# <a name="required-arguments-and-overload-groups"></a>Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar
Etkinlikler, etkinliğin yürütmeye geçerli olması için belirli bağımsız değişkenlerin bağlanması gerektiği için yapılandırılabilir. Özniteliği, bir etkinliğin belirli bağımsız değişkenlerinin gerekli olduğunu `OverloadGroup` ve öznitelik gereken bağımsız değişkenlerin kategorilerini gruplamak için kullanıldığını belirtmek için kullanılır. `RequiredArgument` Etkinlik yazarları, özniteliklerini kullanarak basit veya karmaşık etkinlik doğrulama yapılandırması sağlayabilir.  
  
## <a name="using-required-arguments"></a>Gerekli bağımsız değişkenleri kullanma  
 `RequiredArgument` Özniteliği bir etkinlikte kullanmak için, kullanarak <xref:System.Activities.RequiredArgumentAttribute>istenen bağımsız değişkenleri belirtin. Bu örnekte, iki gerekli `Add` bağımsız değişkene sahip bir etkinlik tanımlanmıştır.  
  
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
  
 XAML 'de, gereken bağımsız değişkenler de kullanılarak <xref:System.Activities.RequiredArgumentAttribute>belirtilir. Bu örnekte, `Add` etkinlik üç bağımsız değişken kullanılarak tanımlanır ve ekleme işlemini gerçekleştirmek için <xref:System.Activities.Statements.Assign%601> bir etkinlik kullanır.  
  
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
  
 Etkinlik kullanılıyorsa ve gerekli bağımsız değişkenlerden herhangi biri bağlanmazsa, aşağıdaki doğrulama hatası döndürülür.  
  
 **Gerekli ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  
> [!NOTE]
> Doğrulama hatalarını ve uyarılarını denetleme ve işleme hakkında daha fazla bilgi için bkz. [etkinlik doğrulamasını çağırma](invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Aşırı yükleme grupları kullanma

Aşırı yükleme grupları, bir etkinlikte hangi bağımsız değişken birleşimlerinin geçerli olduğunu belirten bir yöntem sağlar. Bağımsız değişkenler kullanılarak <xref:System.Activities.OverloadGroupAttribute>birlikte gruplandırılır. Her gruba tarafından <xref:System.Activities.OverloadGroupAttribute>belirtilen bir ad verilir. Etkinlik, aşırı yükleme grubundaki yalnızca bir bağımsız değişken kümesi bağlandığında geçerlidir. Aşağıdaki örnekte, bir `CreateLocation` sınıf tanımlanmıştır.  
  
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
  
 Bu etkinliğin amacı, ABD 'de bir konum belirtmektir. Bunu yapmak için, etkinliğin kullanıcısı üç bağımsız değişken grubundan birini kullanarak konumu belirtebilir. Bağımsız değişkenlerin geçerli birleşimlerini belirtmek için, üç aşırı yükleme grubu tanımlanmıştır. `G1``Latitude` ve`Longitude` bağımsız değişkenlerini içerir. `G2`, `Street` ,`City` ve`State`içerir. `G3``Street` ve`Zip`içerir. `Name`Ayrıca gerekli bir bağımsız değişkendir, ancak aşırı yükleme grubunun bir parçası değildir. Bu etkinliğin geçerli `Name` olması için bir ve yalnızca bir aşırı yükleme grubundaki tüm bağımsız değişkenlerle birlikte bağlanması gerekir.  
  
 Aşağıdaki örnekte, [veritabanı erişim etkinlikleri](./samples/database-access-activities.md) örneğinden alınan iki aşırı yükleme grubu vardır: `ConnectionString` ve. `ConfigFileSectionName` Bu etkinliğin geçerli `ProviderName` olması için, ve `ConnectionString` bağımsız değişkenlerin bir veya `ConfigName` bağımsız değişken olması gerekir, ancak her ikisine birden değil.  
  
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
  
 Aşırı yükleme grubu tanımlarken:  
  
- Aşırı yükleme grubu, başka bir aşırı yükleme grubunun alt kümesi veya eşdeğer bir kümesi olamaz.  
  
    > [!NOTE]
    > Bu kural için bir özel durum var. Bir aşırı yükleme grubu başka bir aşırı yükleme grubunun alt kümesiyse ve alt küme yalnızca olduğu bağımsız değişkenleri `RequiredArgument` `false`içeriyorsa, aşırı yükleme grubu geçerli olur.  
  
- Aşırı yükleme grupları örtüşüyor, ancak grupların kesişimi bir veya her ikisinin de aşırı yükleme grubunun tüm gerekli bağımsız değişkenlerini içeriyorsa, bu bir hatadır. Önceki örnekte `G2` , ve `G3` aşırı yükleme grupları örtüşüyor, ancak kesişme, bir grubun tüm bağımsız değişkenlerini içermediğinden bu geçerli olduğundan  
  
 Bir aşırı yükleme grubundaki bağımsız değişkenleri bağlamada:  
  
- Gruptaki tüm `RequiredArgument` bağımsız değişkenler bağlıysa, aşırı yükleme grubu, bağlantılı olarak değerlendirilir.  
  
- Bir grupta sıfır `RequiredArgument` bağımsız değişken ve en az bir bağımsız değişken varsa, Grup, bağlantılı olarak kabul edilir.  
  
- Bir aşırı yükleme grubunun hiçbir bağımsız değişkeni yoksa `RequiredArgument` , hiçbir aşırı yükleme grubu bağlanmamışsa, bu bir doğrulama hatasıdır.  
  
- Birden fazla aşırı yükleme grubuna sahip olması hatadır, diğer bir deyişle, bir aşırı yükleme grubundaki tüm gerekli bağımsız değişkenler bağlanır ve başka bir aşırı yükleme grubundaki herhangi bir bağımsız değişken de bağlanır.
