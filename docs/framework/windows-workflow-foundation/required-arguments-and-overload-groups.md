---
title: Gerekli bağımsız değişkenler ve aşırı yüklenmiş gruplar
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: d7cfe00d93f1eede77bcda5881c63843722c9a17
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452907"
---
# <a name="required-arguments-and-overload-groups"></a>Gerekli bağımsız değişkenler ve aşırı yüklenmiş gruplar
Etkinlikleri belirli bağımsız değişkenler etkinliğinin yürütme için geçerli olacak şekilde bağlanması için gerekli olacak şekilde yapılandırılabilir. `RequiredArgument` Özniteliği, belirli bir etkinliğin bağımsız gerekli olduğunu belirtmek için kullanılır ve `OverloadGroup` öznitelik gerekli bağımsız değişken kategorisi gruplamak için kullanılır. Öznitelikleri kullanarak etkinlik yazarlar basit veya karmaşık etkinlik doğrulama yapılandırmaları sağlayabilir.  
  
## <a name="using-required-arguments"></a>Gerekli bağımsız değişkenleri kullanma  
 Kullanılacak `RequiredArgument` özniteliği bir etkinlik, belirtmek istediğiniz bağımsız değişkenleri kullanarak <xref:System.Activities.RequiredArgumentAttribute>. Bu örnekte, bir `Add` etkinlik, iki bağımsız değişkenler zorunludur tanımlanır.  
  
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
  
 XAML içinde gerekli bağımsız değişkenler de kullanarak belirtilen <xref:System.Activities.RequiredArgumentAttribute>. Bu örnekte `Add` etkinlik üç bağımsız değişken ve kullandığı kullanılarak tanımlanmış bir <xref:System.Activities.Statements.Assign%601> ekleme işlemi gerçekleştirmek için etkinlik.  
  
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
  
 Etkinliği kullanılır ve gerekli bağımsız değişken ya da değil bağlı aşağıdaki doğrulama hatası döndürülür.  
  
 **Povinný argument 'İşlenen1' için değer sağlanmadı.**  
> [!NOTE]
> Denetleme ve doğrulama hataları ve Uyarıları işleme hakkında daha fazla bilgi için bkz. [etkinlik doğrulamayı çağırma](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Aşırı yüklenmiş gruplar kullanma

Aşırı yüklenmiş gruplar engellenecek bağımsız değişkenleri olan bir etkinlikte geçerli olduğunu belirten bir yöntem sağlar. Bağımsız değişkenler arada gruplandırılır kullanarak <xref:System.Activities.OverloadGroupAttribute>. Her grubu tarafından belirtilen bir ad verilir <xref:System.Activities.OverloadGroupAttribute>. Etkinlik, tek bir bağımsız değişken kümesinin bir aşırı yükleme grubuna bağlı olduğunda geçerlidir. Aşağıdaki örnekte, bir `CreateLocation` sınıfı tanımlanır.  
  
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
  
 Amacı, bu etkinlik bir konuma ABD'de belirtmektir. Bunu yapmak için kullanıcı etkinliğinin üç bağımsız değişken grupları kullanarak konumu belirtebilirsiniz. Bağımsız değişkenlerin geçerli birleşimleri belirtmek için üç aşırı yüklenmiş gruplar tanımlanır. `G1` içeren `Latitude` ve `Longitude` bağımsız değişkenler. `G2` içeren `Street`, `City`, ve `State`. `G3` içeren `Street` ve `Zip`. `Name` Ayrıca gerekli bir bağımsız değişkendir, ancak bir aşırı yükleme grubunun parçası değil. Geçerli olması bu etkinliği `Name` tüm bağımsız değişkenleri ile birlikte bir ve yalnızca bir aşırı yükleme grubundan bağlanması gerekir.  
  
 Aşağıdaki örnekte, geçen gelen [veritabanı erişimi etkinlikleri](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) örnek, aşırı yükleme iki grup vardır: `ConnectionString` ve `ConfigFileSectionName`. Ya da geçerli olması bu etkinliği `ProviderName` ve `ConnectionString` bağımsız değişkenleri ilişkili olmalıdır, veya `ConfigName` bağımsız değişkeni, ancak ikisine birden değil.  
  
```  
Public class DbUpdate: AsyncCodeActivity  
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
  
-   Bir aşırı yükleme grubu bir alt veya başka bir aşırı yükleme grubu eşdeğer bir dizi olamaz.  
  
    > [!NOTE]
    >  Bu kuralın tek istisnası yoktur. Aşırı yükleme grubu başka bir aşırı yükleme grubu bir alt kümesidir ve alt yalnızca bağımsız değişken varsa burada `RequiredArgument` olduğu `false`, aşırı yükleme grubu geçerli ise.  
  
-   Aşırı yüklenmiş gruplar binebilir ancak kesişimi gruplarının birini veya ikisini de aşırı yüklenmiş gruplar tüm gerekli bağımsız içeriyorsa bir hata değildir. Önceki örnekte `G2` ve `G3` grupları çakışan aşırı yükleme, ancak bir ya da hem de grupların tüm bağımsız değişkenler kesişimi içermediğinden, bu geçerli.  
  
 Bağımsız değişken bir aşırı yükleme grubunda bağlanırken:  
  
-   Aşırı yükleme grubunun ilişkili tüm kabul edildiği `RequiredArgument` bağımsız değişken grubunda bağlıdır.  
  
-   Bir grubu sıfır varsa `RequiredArgument` bağımsız değişkenleri ve en az bir bağımsız değişken bağlı, sonra Grup bağlı olarak kabul edilir.  
  
-   Bir doğrulama hatası olduğu sürece bir aşırı yükleme grubu olmayan hiçbir aşırı yüklenmiş gruplar bağlıysa `RequiredArgument` da bağımsız değişkenler.  
  
-   Bağlı, birden fazla aşırı yükleme grubu için bir hata olduğunu, aşırı yüklemelerden birine grubundaki tüm gerekli bağımsız değişkenler bağlıdır ve başka bir aşırı yükleme grubundaki herhangi bir bağımsız değişken de bağlıdır.
