---
title: "Gerekli bağımsız değişkenleri ve aşırı grupları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fae9759faa6ae5e2fa65417c6ef5767330f6d9c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="required-arguments-and-overload-groups"></a>Gerekli bağımsız değişkenleri ve aşırı grupları
Böylece bazı bağımsız değişkenler için yürütme geçerli olması etkinliği bağlanması için gerekli olan etkinlikleri yapılandırılabilir. `RequiredArgument` Özniteliği bazı bağımsız değişkenler bir etkinlikte gerekli olduğunu belirtmek için kullanılır ve `OverloadGroup` özniteliği gerekli bağımsız kategorilerini gruplamak için kullanılır. Öznitelikleri kullanarak, etkinlik yazarlar basit veya karmaşık etkinlik doğrulama yapılandırmaları sağlayabilir.  
  
## <a name="using-required-arguments"></a>Gerekli bağımsız değişkenleri kullanma  
 Kullanılacak `RequiredArgument` özniteliği bir etkinlikte, kullanmak istediğiniz bağımsız değişkenleri belirtmek <xref:System.Activities.RequiredArgumentAttribute>. Bu örnekte, bir `Add` etkinlik tanımlanmış iki bağımsız değişken gerektirir.  
  
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
  
 XAML'de gerekli bağımsız değişkenler de kullanarak belirtilir <xref:System.Activities.RequiredArgumentAttribute>. Bu örnekte `Add` etkinlik üç bağımsız değişkenleri ve kullandığı kullanılarak tanımlanmış bir <xref:System.Activities.Statements.Assign%601> ekleme işlemi gerçekleştirme etkinliği.  
  
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
  
 Etkinlik kullanılıyorsa ve gerekli bağımsız değişkenlerin ya da bağlı olmayan aşağıdaki doğrulama hatasını döndürdü.  
  
 **Gerekli etkinlik bağımsız değişkeni 'Operand1' için değer girilmedi.**  
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]denetleme ve doğrulama hataları ve Uyarıları işleme hakkında bkz: [çağırma etkinlik doğrulama](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Aşırı grupları kullanma  
 Aşırı grupları engellenecek bağımsız olan bir etkinlikte geçerli olmadığını belirten bir yöntem sağlar. Bağımsız değişkenler gruplandırılır birlikte kullanarak <xref:System.Activities.OverloadGroupAttribute>. Her grubu tarafından belirtilen bir ad verilir <xref:System.Activities.OverloadGroupAttribute>, etkinlik bir aşırı yüklemesini grubundaki bağımsız değişkenler tek kümesine bağlı olduğunda geçerlidir. Aşağıdaki örnekte, geçen [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) örnek, bir `CreateLocation` sınıfı tanımlanır.  
  
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
  
 ABD'de bir konum belirtmek için bu etkinliği amacı olan. Bunu yapmak için kullanıcı etkinliğinin bağımsız değişkenlerinin üç gruplarından birini kullanarak konum belirtebilirsiniz. Bağımsız değişkenler geçerli birleşimlerini belirtmek için üç aşırı grupları tanımlanır. `G1`içeren `Latitude` ve `Longitude` bağımsız değişkenler. `G2`içeren `Street`, `City`, ve `State`. `G3`içeren `Street` ve `Zip`. `Name`da gerekli bir bağımsız değişken, ancak bir aşırı yüklemesini grubunun bir parçası değil. Geçerli olması bu etkinliği `Name` tüm bağımsız değişkenler ile birlikte tek bir aşırı yüklemesini grubundan bağlanması gerekir.  
  
 Aşağıdaki örnekte, geçen [veritabanı erişimi etkinliklerini](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) örnek, iki aşırı grupları vardır: `ConnectionString` ve `ConfigFileSectionName`. Ya da geçerli olması bu etkinliği `ProviderName` ve `ConnectionString` bağımsız değişkenleri bağlı olmalıdır, veya `ConfigName` bağımsız değişkeni, ancak ikisini birden değil.  
  
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
  
 Aşırı Grup tanımlarken:  
  
-   Aşırı grubu, bir alt veya başka bir aşırı yüklemesini Grup eşdeğer bir dizi olamaz.  
  
    > [!NOTE]
    >  Bu kural için bir istisna vardır. Başka bir aşırı yüklemesini grubun alt kümesini aşırı grubudur ve yalnızca bağımsız değişken alt içeriyorsa nerede `RequiredArgument` olan `false`, aşırı Grup geçerli olur.  
  
-   Aşırı grupları binebilir ancak grupları kesişimi tüm gerekli bağımsız birini veya her ikisini aşırı grupları içeriyorsa bir hata değildir. Önceki örnekte `G2` ve `G3` çakışan grupları aşırı ancak kesişimi birine veya ikisine de grupları, tüm bağımsız değişkenler içermediğinden Bu geçerli.  
  
 Bağımsız değişkenler bir aşırı yüklemesini grubunda bağlanırken:  
  
-   Aşırı Grup bağlı olarak tüm değerlendirilir `RequiredArgument` Grup değişkenlerinde bağlıdır.  
  
-   Bir grup sıfır varsa `RequiredArgument` bağımsız değişkenleri ve en az bir değişken bağlı, sonra da Grup bağlı olarak kabul edilir.  
  
-   Bir aşırı yüklemesini Grup no olmadıkça hiçbir aşırı yüklemesi grupları bağlıysa bir doğrulama hatası olan `RequiredArgument` da bağımsız değişkenler.  
  
-   Bağlı, birden fazla aşırı grup için bir hata olduğundan, aşırı yüklemesiyle grubundaki tüm gerekli bağımsız bağlı olan ve başka bir aşırı yüklemesini grubunda herhangi bir bağımsız değişken de bağlıdır.
