---
title: Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: b5006a201ce5db68e925bd5764fadde308bbccb4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937793"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="68eeb-102">Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar</span><span class="sxs-lookup"><span data-stu-id="68eeb-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="68eeb-103">Etkinlikleri belirli bağımsız değişkenler etkinliğinin yürütme için geçerli olacak şekilde bağlanması için gerekli olacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="68eeb-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="68eeb-104">`RequiredArgument` Özniteliği, belirli bir etkinliğin bağımsız gerekli olduğunu belirtmek için kullanılır ve `OverloadGroup` öznitelik gerekli bağımsız değişken kategorisi gruplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="68eeb-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="68eeb-105">Öznitelikleri kullanarak etkinlik yazarlar basit veya karmaşık etkinlik doğrulama yapılandırmaları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="68eeb-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="68eeb-106">Gerekli bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="68eeb-106">Using Required Arguments</span></span>  
 <span data-ttu-id="68eeb-107">Kullanılacak `RequiredArgument` özniteliği bir etkinlik, belirtmek istediğiniz bağımsız değişkenleri kullanarak <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="68eeb-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="68eeb-108">Bu örnekte, bir `Add` etkinlik, iki bağımsız değişkenler zorunludur tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="68eeb-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="68eeb-109">XAML içinde gerekli bağımsız değişkenler de kullanarak belirtilen <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="68eeb-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="68eeb-110">Bu örnekte `Add` etkinlik üç bağımsız değişken ve kullandığı kullanılarak tanımlanmış bir <xref:System.Activities.Statements.Assign%601> ekleme işlemi gerçekleştirmek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="68eeb-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
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
  
 <span data-ttu-id="68eeb-111">Etkinliği kullanılır ve gerekli bağımsız değişken ya da değil bağlı aşağıdaki doğrulama hatası döndürülür.</span><span class="sxs-lookup"><span data-stu-id="68eeb-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="68eeb-112">**Povinný argument 'İşlenen1' için değer sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="68eeb-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="68eeb-113">Denetleme ve doğrulama hataları ve Uyarıları işleme hakkında daha fazla bilgi için bkz. [etkinlik doğrulamayı çağırma](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="68eeb-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="68eeb-114">Aşırı yüklenmiş gruplar kullanma</span><span class="sxs-lookup"><span data-stu-id="68eeb-114">Using Overload Groups</span></span>

<span data-ttu-id="68eeb-115">Aşırı yüklenmiş gruplar engellenecek bağımsız değişkenleri olan bir etkinlikte geçerli olduğunu belirten bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="68eeb-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="68eeb-116">Bağımsız değişkenler arada gruplandırılır kullanarak <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="68eeb-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="68eeb-117">Her grubu tarafından belirtilen bir ad verilir <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="68eeb-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="68eeb-118">Etkinlik, tek bir bağımsız değişken kümesinin bir aşırı yükleme grubuna bağlı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="68eeb-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="68eeb-119">Aşağıdaki örnekte, bir `CreateLocation` sınıfı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="68eeb-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
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
  
 <span data-ttu-id="68eeb-120">Amacı, bu etkinlik bir konuma ABD'de belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="68eeb-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="68eeb-121">Bunu yapmak için kullanıcı etkinliğinin üç bağımsız değişken grupları kullanarak konumu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68eeb-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="68eeb-122">Bağımsız değişkenlerin geçerli birleşimleri belirtmek için üç aşırı yüklenmiş gruplar tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="68eeb-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="68eeb-123">`G1` içeren `Latitude` ve `Longitude` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="68eeb-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="68eeb-124">`G2` içeren `Street`, `City`, ve `State`.</span><span class="sxs-lookup"><span data-stu-id="68eeb-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="68eeb-125">`G3` içeren `Street` ve `Zip`.</span><span class="sxs-lookup"><span data-stu-id="68eeb-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="68eeb-126">`Name` Ayrıca gerekli bir bağımsız değişkendir, ancak bir aşırı yükleme grubunun parçası değil.</span><span class="sxs-lookup"><span data-stu-id="68eeb-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="68eeb-127">Geçerli olması bu etkinliği `Name` tüm bağımsız değişkenleri ile birlikte bir ve yalnızca bir aşırı yükleme grubundan bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="68eeb-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="68eeb-128">Aşağıdaki örnekte, geçen gelen [veritabanı erişimi etkinlikleri](./samples/database-access-activities.md) örnek, aşırı yükleme iki grup vardır: `ConnectionString` ve `ConfigFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="68eeb-128">In the following example, taken from the [Database Access Activities](./samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="68eeb-129">Ya da geçerli olması bu etkinliği `ProviderName` ve `ConnectionString` bağımsız değişkenleri ilişkili olmalıdır, veya `ConfigName` bağımsız değişkeni, ancak ikisine birden değil.</span><span class="sxs-lookup"><span data-stu-id="68eeb-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
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
  
 <span data-ttu-id="68eeb-130">Aşırı yükleme grubu tanımlarken:</span><span class="sxs-lookup"><span data-stu-id="68eeb-130">When defining an overload group:</span></span>  
  
- <span data-ttu-id="68eeb-131">Bir aşırı yükleme grubu bir alt veya başka bir aşırı yükleme grubu eşdeğer bir dizi olamaz.</span><span class="sxs-lookup"><span data-stu-id="68eeb-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="68eeb-132">Bu kuralın tek istisnası yoktur.</span><span class="sxs-lookup"><span data-stu-id="68eeb-132">There is one exception to this rule.</span></span> <span data-ttu-id="68eeb-133">Aşırı yükleme grubu başka bir aşırı yükleme grubu bir alt kümesidir ve alt yalnızca bağımsız değişken varsa burada `RequiredArgument` olduğu `false`, aşırı yükleme grubu geçerli ise.</span><span class="sxs-lookup"><span data-stu-id="68eeb-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
- <span data-ttu-id="68eeb-134">Aşırı yüklenmiş gruplar binebilir ancak kesişimi gruplarının birini veya ikisini de aşırı yüklenmiş gruplar tüm gerekli bağımsız içeriyorsa bir hata değildir.</span><span class="sxs-lookup"><span data-stu-id="68eeb-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="68eeb-135">Önceki örnekte `G2` ve `G3` grupları çakışan aşırı yükleme, ancak bir ya da hem de grupların tüm bağımsız değişkenler kesişimi içermediğinden, bu geçerli.</span><span class="sxs-lookup"><span data-stu-id="68eeb-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="68eeb-136">Bağımsız değişken bir aşırı yükleme grubunda bağlanırken:</span><span class="sxs-lookup"><span data-stu-id="68eeb-136">When binding arguments in an overload group:</span></span>  
  
- <span data-ttu-id="68eeb-137">Aşırı yükleme grubunun ilişkili tüm kabul edildiği `RequiredArgument` bağımsız değişken grubunda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="68eeb-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
- <span data-ttu-id="68eeb-138">Bir grubu sıfır varsa `RequiredArgument` bağımsız değişkenleri ve en az bir bağımsız değişken bağlı, sonra Grup bağlı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="68eeb-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
- <span data-ttu-id="68eeb-139">Bir doğrulama hatası olduğu sürece bir aşırı yükleme grubu olmayan hiçbir aşırı yüklenmiş gruplar bağlıysa `RequiredArgument` da bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="68eeb-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
- <span data-ttu-id="68eeb-140">Bağlı, birden fazla aşırı yükleme grubu için bir hata olduğunu, aşırı yüklemelerden birine grubundaki tüm gerekli bağımsız değişkenler bağlıdır ve başka bir aşırı yükleme grubundaki herhangi bir bağımsız değişken de bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="68eeb-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
