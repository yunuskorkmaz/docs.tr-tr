---
title: Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 452285b1f5b73ecf75fc50f59365aa2633f26e42
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245880"
---
# <a name="required-arguments-and-overload-groups"></a>Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar

Etkinlikler, etkinliğin yürütmeye geçerli olması için belirli bağımsız değişkenlerin bağlanması gerektiği için yapılandırılabilir. `RequiredArgument`Özniteliği, bir etkinliğin belirli bağımsız değişkenlerinin gerekli olduğunu ve `OverloadGroup` öznitelik gereken bağımsız değişkenlerin kategorilerini gruplamak için kullanıldığını belirtmek için kullanılır. Etkinlik yazarları, özniteliklerini kullanarak basit veya karmaşık etkinlik doğrulama yapılandırması sağlayabilir.  
  
## <a name="using-required-arguments"></a>Gerekli bağımsız değişkenleri kullanma  

 `RequiredArgument`Özniteliği bir etkinlikte kullanmak için, kullanarak istenen bağımsız değişkenleri belirtin <xref:System.Activities.RequiredArgumentAttribute> . Bu örnekte, `Add` iki gerekli bağımsız değişkene sahip bir etkinlik tanımlanmıştır.  
  
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
  
 XAML 'de, gereken bağımsız değişkenler de kullanılarak belirtilir <xref:System.Activities.RequiredArgumentAttribute> . Bu örnekte, `Add` etkinlik üç bağımsız değişken kullanılarak tanımlanır ve <xref:System.Activities.Statements.Assign%601> ekleme işlemini gerçekleştirmek için bir etkinlik kullanır.  
  
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

Aşırı yükleme grupları, bir etkinlikte hangi bağımsız değişken birleşimlerinin geçerli olduğunu belirten bir yöntem sağlar. Bağımsız değişkenler kullanılarak birlikte gruplandırılır <xref:System.Activities.OverloadGroupAttribute> . Her gruba tarafından belirtilen bir ad verilir <xref:System.Activities.OverloadGroupAttribute> . Etkinlik, aşırı yükleme grubundaki yalnızca bir bağımsız değişken kümesi bağlandığında geçerlidir. Aşağıdaki örnekte, bir `CreateLocation` sınıf tanımlanmıştır.  
  
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
  
 Bu etkinliğin amacı, ABD 'de bir konum belirtmektir. Bunu yapmak için, etkinliğin kullanıcısı üç bağımsız değişken grubundan birini kullanarak konumu belirtebilir. Bağımsız değişkenlerin geçerli birleşimlerini belirtmek için, üç aşırı yükleme grubu tanımlanmıştır. `G1``Latitude`ve `Longitude` bağımsız değişkenlerini içerir. `G2``Street`, `City` , ve içerir `State` . `G3``Street`ve içerir `Zip` . `Name` Ayrıca gerekli bir bağımsız değişkendir, ancak aşırı yükleme grubunun bir parçası değildir. Bu etkinliğin geçerli olması için `Name` bir ve yalnızca bir aşırı yükleme grubundaki tüm bağımsız değişkenlerle birlikte bağlanması gerekir.  
  
 Aşağıdaki örnekte, [veritabanı erişim etkinlikleri](./samples/database-access-activities.md) örneğinden alınan iki aşırı yükleme grubu vardır: `ConnectionString` ve `ConfigFileSectionName` . Bu etkinliğin geçerli olması için, `ProviderName` ve `ConnectionString` bağımsız değişkenlerin bir veya bağımsız değişken olması gerekir, `ConfigName` ancak her ikisine birden değil.  
  
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
    > Bu kural için bir özel durum var. Bir aşırı yükleme grubu başka bir aşırı yükleme grubunun alt kümesiyse ve alt küme yalnızca olduğu bağımsız değişkenleri `RequiredArgument` içeriyorsa `false` , aşırı yükleme grubu geçerli olur.  
  
- Aşırı yükleme grupları örtüşüyor, ancak grupların kesişimi bir veya her ikisinin de aşırı yükleme grubunun tüm gerekli bağımsız değişkenlerini içeriyorsa, bu bir hatadır. Önceki örnekte, `G2` ve `G3` aşırı yükleme grupları örtüşüyor, ancak kesişme, bir grubun tüm bağımsız değişkenlerini içermediğinden bu geçerli olduğundan  
  
 Bir aşırı yükleme grubundaki bağımsız değişkenleri bağlamada:  
  
- Gruptaki tüm bağımsız değişkenler bağlıysa, aşırı yükleme grubu, bağlantılı olarak değerlendirilir `RequiredArgument` .  
  
- Bir grupta sıfır `RequiredArgument` bağımsız değişken ve en az bir bağımsız değişken varsa, Grup, bağlantılı olarak kabul edilir.  
  
- Bir aşırı yükleme grubunun hiçbir bağımsız değişkeni yoksa, hiçbir aşırı yükleme grubu bağlanmamışsa, bu bir doğrulama hatasıdır `RequiredArgument` .  
  
- Birden fazla aşırı yükleme grubuna sahip olması hatadır, diğer bir deyişle, bir aşırı yükleme grubundaki tüm gerekli bağımsız değişkenler bağlanır ve başka bir aşırı yükleme grubundaki herhangi bir bağımsız değişken de bağlanır.
