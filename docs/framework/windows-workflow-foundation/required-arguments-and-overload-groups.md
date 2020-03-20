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
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="44f17-102">Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar</span><span class="sxs-lookup"><span data-stu-id="44f17-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="44f17-103">Etkinlikler, belirli bağımsız değişkenlerin yürütme için geçerli olması için belirli bağımsız değişkenlerin bağlanması için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="44f17-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="44f17-104">Öznitelik, `RequiredArgument` bir etkinlikteki belirli bağımsız değişkenlerin gerekli `OverloadGroup` olduğunu ve öznitelik in gerekli bağımsız değişkenkategorilerini birlikte gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44f17-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="44f17-105">İşleçlik leri kullanarak, etkinlik yazarları basit veya karmaşık etkinlik doğrulama yapılandırmaları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="44f17-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="44f17-106">Gerekli Bağımsız Değişkenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="44f17-106">Using Required Arguments</span></span>  
 <span data-ttu-id="44f17-107">Bir etkinlikte `RequiredArgument` öznitelik kullanmak için, kullanarak <xref:System.Activities.RequiredArgumentAttribute>istenen bağımsız değişkenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="44f17-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="44f17-108">Bu örnekte, `Add` iki gerekli bağımsız değişkeni olan bir etkinlik tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="44f17-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="44f17-109">XAML'de gerekli bağımsız değişkenler <xref:System.Activities.RequiredArgumentAttribute>de kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="44f17-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="44f17-110">Bu örnekte `Add` etkinlik üç bağımsız değişken kullanılarak <xref:System.Activities.Statements.Assign%601> tanımlanır ve ekleme işlemini gerçekleştirmek için bir etkinlik kullanır.</span><span class="sxs-lookup"><span data-stu-id="44f17-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
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
  
 <span data-ttu-id="44f17-111">Etkinlik kullanılırsa ve gerekli bağımsız değişkenlerden biri bağlı değilse aşağıdaki doğrulama hatası döndürülür.</span><span class="sxs-lookup"><span data-stu-id="44f17-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="44f17-112">**Gerekli bir etkinlik bağımsız değişkeni 'Operand1' için değer verilmedi.**</span><span class="sxs-lookup"><span data-stu-id="44f17-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="44f17-113">Doğrulama hatalarını ve uyarılarını denetleme ve işleme hakkında daha fazla bilgi için [bkz.](invoking-activity-validation.md)</span><span class="sxs-lookup"><span data-stu-id="44f17-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="44f17-114">Aşırı Yük Gruplarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="44f17-114">Using Overload Groups</span></span>

<span data-ttu-id="44f17-115">Aşırı yükleme grupları, bir etkinlikte hangi bağımsız değişken birleşimlerinin geçerli olduğunu belirtmek için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="44f17-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="44f17-116">Bağımsız değişkenler kullanılarak <xref:System.Activities.OverloadGroupAttribute>birlikte gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="44f17-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="44f17-117">Her gruba <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="44f17-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="44f17-118">Etkinlik, aşırı yükleme grubundaki yalnızca bir bağımsız değişken kümesi bağlı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="44f17-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="44f17-119">Aşağıdaki örnekte, `CreateLocation` bir sınıf tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="44f17-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
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
  
 <span data-ttu-id="44f17-120">Bu etkinliğin amacı, ABD'de bir konum belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="44f17-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="44f17-121">Bunu yapmak için, etkinliğin kullanıcı bağımsız değişkenler üç grup birini kullanarak konumu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44f17-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="44f17-122">Bağımsız değişkenlerin geçerli birleşimlerini belirtmek için üç aşırı yükleme grubu tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="44f17-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="44f17-123">`G1``Latitude` ve `Longitude` bağımsız değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="44f17-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="44f17-124">`G2`içerir `Street` `City`, `State`ve .</span><span class="sxs-lookup"><span data-stu-id="44f17-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="44f17-125">`G3`içerir `Street` `Zip`ve .</span><span class="sxs-lookup"><span data-stu-id="44f17-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="44f17-126">`Name`ayrıca gerekli bir bağımsız değişkendir, ancak aşırı yükleme grubunun bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="44f17-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="44f17-127">Bu etkinliğin geçerli olabilmek için, `Name` bir ve yalnızca bir aşırı yükleme grubundaki tüm bağımsız değişkenlerle birbirine bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44f17-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="44f17-128">[Veritabanı Erişim Etkinlikleri](./samples/database-access-activities.md) örneğinden alınan aşağıdaki örnekte, iki aşırı `ConnectionString` `ConfigFileSectionName`yükleme grubu vardır: ve .</span><span class="sxs-lookup"><span data-stu-id="44f17-128">In the following example, taken from the [Database Access Activities](./samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="44f17-129">Bu etkinliğin geçerli olabilmesi `ProviderName` için, `ConnectionString` bağımsız değişkenler `ConfigName` veya bağımsız değişkenin bağlı olması gerekir, ancak her ikisi de geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="44f17-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
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
  
 <span data-ttu-id="44f17-130">Aşırı yükleme grubu tanımlanırken:</span><span class="sxs-lookup"><span data-stu-id="44f17-130">When defining an overload group:</span></span>  
  
- <span data-ttu-id="44f17-131">Aşırı yükleme grubu bir alt küme veya başka bir aşırı yük grubunun eşdeğer kümesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="44f17-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="44f17-132">Bu kuralın bir istisnası vardır.</span><span class="sxs-lookup"><span data-stu-id="44f17-132">There is one exception to this rule.</span></span> <span data-ttu-id="44f17-133">Aşırı yük grubu başka bir aşırı yük grubunun alt kümesiyse ve `RequiredArgument` alt `false`küme yalnızca aşırı yükleme grubunun geçerli olduğu bağımsız değişkenleri içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="44f17-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
- <span data-ttu-id="44f17-134">Aşırı yük grupları çakışabilir, ancak grupların kesişimi aşırı yük gruplarından birinin veya her ikisinin gerekli tüm bağımsız değişkenlerini içeriyorsa bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="44f17-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="44f17-135">Önceki örnekte `G2` ve `G3` aşırı yükleme grupları çakıştı, ancak kesişim bir veya her iki grubun tüm bağımsız değişkenlerini içermediğinden bu geçerliydi.</span><span class="sxs-lookup"><span data-stu-id="44f17-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="44f17-136">Bir aşırı yük grubunda bağımsız değişkenler bağlanırken:</span><span class="sxs-lookup"><span data-stu-id="44f17-136">When binding arguments in an overload group:</span></span>  
  
- <span data-ttu-id="44f17-137">Gruptaki tüm `RequiredArgument` bağımsız değişkenler bağlıysa, aşırı yükleme grubu bağlı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="44f17-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
- <span data-ttu-id="44f17-138">Bir grubun sıfır `RequiredArgument` bağımsız değişkeni varsa ve en az bir bağımsız değişken bağlıysa, grup bağlı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="44f17-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
- <span data-ttu-id="44f17-139">Bir aşırı yük grubunda bağımsız değişken yoksa, `RequiredArgument` aşırı yük grupları bağlı değilse, bir doğrulama hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="44f17-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
- <span data-ttu-id="44f17-140">Birden fazla aşırı yük grubuna bağlı olması bir hatadır, yani bir aşırı yük grubundaki tüm gerekli bağımsız değişkenler bağlanır ve başka bir aşırı yükleme grubundaki herhangi bir bağımsız değişken de bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="44f17-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
