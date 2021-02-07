---
description: 'Daha fazla bilgi edinin: gerekli bağımsız değişkenler ve aşırı yükleme grupları'
title: Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 1eea77276ad976c81d891e45cfbe5217b298b4fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720039"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="caea2-103">Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar</span><span class="sxs-lookup"><span data-stu-id="caea2-103">Required Arguments and Overload Groups</span></span>

<span data-ttu-id="caea2-104">Etkinlikler, etkinliğin yürütmeye geçerli olması için belirli bağımsız değişkenlerin bağlanması gerektiği için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="caea2-104">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="caea2-105">`RequiredArgument`Özniteliği, bir etkinliğin belirli bağımsız değişkenlerinin gerekli olduğunu ve `OverloadGroup` öznitelik gereken bağımsız değişkenlerin kategorilerini gruplamak için kullanıldığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="caea2-105">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="caea2-106">Etkinlik yazarları, özniteliklerini kullanarak basit veya karmaşık etkinlik doğrulama yapılandırması sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="caea2-106">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="caea2-107">Gerekli bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="caea2-107">Using Required Arguments</span></span>  

 <span data-ttu-id="caea2-108">`RequiredArgument`Özniteliği bir etkinlikte kullanmak için, kullanarak istenen bağımsız değişkenleri belirtin <xref:System.Activities.RequiredArgumentAttribute> .</span><span class="sxs-lookup"><span data-stu-id="caea2-108">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="caea2-109">Bu örnekte, `Add` iki gerekli bağımsız değişkene sahip bir etkinlik tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="caea2-109">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="caea2-110">XAML 'de, gereken bağımsız değişkenler de kullanılarak belirtilir <xref:System.Activities.RequiredArgumentAttribute> .</span><span class="sxs-lookup"><span data-stu-id="caea2-110">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="caea2-111">Bu örnekte, `Add` etkinlik üç bağımsız değişken kullanılarak tanımlanır ve <xref:System.Activities.Statements.Assign%601> ekleme işlemini gerçekleştirmek için bir etkinlik kullanır.</span><span class="sxs-lookup"><span data-stu-id="caea2-111">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
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
  
 <span data-ttu-id="caea2-112">Etkinlik kullanılıyorsa ve gerekli bağımsız değişkenlerden herhangi biri bağlanmazsa, aşağıdaki doğrulama hatası döndürülür.</span><span class="sxs-lookup"><span data-stu-id="caea2-112">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="caea2-113">**Gerekli ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="caea2-113">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="caea2-114">Doğrulama hatalarını ve uyarılarını denetleme ve işleme hakkında daha fazla bilgi için bkz. [etkinlik doğrulamasını çağırma](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="caea2-114">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="caea2-115">Aşırı yükleme grupları kullanma</span><span class="sxs-lookup"><span data-stu-id="caea2-115">Using Overload Groups</span></span>

<span data-ttu-id="caea2-116">Aşırı yükleme grupları, bir etkinlikte hangi bağımsız değişken birleşimlerinin geçerli olduğunu belirten bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="caea2-116">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="caea2-117">Bağımsız değişkenler kullanılarak birlikte gruplandırılır <xref:System.Activities.OverloadGroupAttribute> .</span><span class="sxs-lookup"><span data-stu-id="caea2-117">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="caea2-118">Her gruba tarafından belirtilen bir ad verilir <xref:System.Activities.OverloadGroupAttribute> .</span><span class="sxs-lookup"><span data-stu-id="caea2-118">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="caea2-119">Etkinlik, aşırı yükleme grubundaki yalnızca bir bağımsız değişken kümesi bağlandığında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="caea2-119">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="caea2-120">Aşağıdaki örnekte, bir `CreateLocation` sınıf tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="caea2-120">In the following example, a `CreateLocation` class is defined.</span></span>  
  
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
  
 <span data-ttu-id="caea2-121">Bu etkinliğin amacı, ABD 'de bir konum belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="caea2-121">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="caea2-122">Bunu yapmak için, etkinliğin kullanıcısı üç bağımsız değişken grubundan birini kullanarak konumu belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="caea2-122">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="caea2-123">Bağımsız değişkenlerin geçerli birleşimlerini belirtmek için, üç aşırı yükleme grubu tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="caea2-123">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="caea2-124">`G1``Latitude`ve `Longitude` bağımsız değişkenlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="caea2-124">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="caea2-125">`G2``Street`, `City` , ve içerir `State` .</span><span class="sxs-lookup"><span data-stu-id="caea2-125">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="caea2-126">`G3``Street`ve içerir `Zip` .</span><span class="sxs-lookup"><span data-stu-id="caea2-126">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="caea2-127">`Name` Ayrıca gerekli bir bağımsız değişkendir, ancak aşırı yükleme grubunun bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="caea2-127">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="caea2-128">Bu etkinliğin geçerli olması için `Name` bir ve yalnızca bir aşırı yükleme grubundaki tüm bağımsız değişkenlerle birlikte bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="caea2-128">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="caea2-129">Aşağıdaki örnekte, [veritabanı erişim etkinlikleri](./samples/database-access-activities.md) örneğinden alınan iki aşırı yükleme grubu vardır: `ConnectionString` ve `ConfigFileSectionName` .</span><span class="sxs-lookup"><span data-stu-id="caea2-129">In the following example, taken from the [Database Access Activities](./samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="caea2-130">Bu etkinliğin geçerli olması için, `ProviderName` ve `ConnectionString` bağımsız değişkenlerin bir veya bağımsız değişken olması gerekir, `ConfigName` ancak her ikisine birden değil.</span><span class="sxs-lookup"><span data-stu-id="caea2-130">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
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
  
 <span data-ttu-id="caea2-131">Aşırı yükleme grubu tanımlarken:</span><span class="sxs-lookup"><span data-stu-id="caea2-131">When defining an overload group:</span></span>  
  
- <span data-ttu-id="caea2-132">Aşırı yükleme grubu, başka bir aşırı yükleme grubunun alt kümesi veya eşdeğer bir kümesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="caea2-132">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="caea2-133">Bu kural için bir özel durum var.</span><span class="sxs-lookup"><span data-stu-id="caea2-133">There is one exception to this rule.</span></span> <span data-ttu-id="caea2-134">Bir aşırı yükleme grubu başka bir aşırı yükleme grubunun alt kümesiyse ve alt küme yalnızca olduğu bağımsız değişkenleri `RequiredArgument` içeriyorsa `false` , aşırı yükleme grubu geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="caea2-134">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
- <span data-ttu-id="caea2-135">Aşırı yükleme grupları örtüşüyor, ancak grupların kesişimi bir veya her ikisinin de aşırı yükleme grubunun tüm gerekli bağımsız değişkenlerini içeriyorsa, bu bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="caea2-135">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="caea2-136">Önceki örnekte, `G2` ve `G3` aşırı yükleme grupları örtüşüyor, ancak kesişme, bir grubun tüm bağımsız değişkenlerini içermediğinden bu geçerli olduğundan</span><span class="sxs-lookup"><span data-stu-id="caea2-136">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="caea2-137">Bir aşırı yükleme grubundaki bağımsız değişkenleri bağlamada:</span><span class="sxs-lookup"><span data-stu-id="caea2-137">When binding arguments in an overload group:</span></span>  
  
- <span data-ttu-id="caea2-138">Gruptaki tüm bağımsız değişkenler bağlıysa, aşırı yükleme grubu, bağlantılı olarak değerlendirilir `RequiredArgument` .</span><span class="sxs-lookup"><span data-stu-id="caea2-138">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
- <span data-ttu-id="caea2-139">Bir grupta sıfır `RequiredArgument` bağımsız değişken ve en az bir bağımsız değişken varsa, Grup, bağlantılı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="caea2-139">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
- <span data-ttu-id="caea2-140">Bir aşırı yükleme grubunun hiçbir bağımsız değişkeni yoksa, hiçbir aşırı yükleme grubu bağlanmamışsa, bu bir doğrulama hatasıdır `RequiredArgument` .</span><span class="sxs-lookup"><span data-stu-id="caea2-140">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
- <span data-ttu-id="caea2-141">Birden fazla aşırı yükleme grubuna sahip olması hatadır, diğer bir deyişle, bir aşırı yükleme grubundaki tüm gerekli bağımsız değişkenler bağlanır ve başka bir aşırı yükleme grubundaki herhangi bir bağımsız değişken de bağlanır.</span><span class="sxs-lookup"><span data-stu-id="caea2-141">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
