---
title: Özellik yükseltme etkinliği
ms.date: 03/30/2017
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
ms.openlocfilehash: 6e059a0d344e6c62833feaa890c459c141a49673
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870090"
---
# <a name="property-promotion-activity"></a><span data-ttu-id="ced3b-102">Özellik yükseltme etkinliği</span><span class="sxs-lookup"><span data-stu-id="ced3b-102">Property Promotion Activity</span></span>
<span data-ttu-id="ced3b-103">Bu örnek sağlayan tümleşik bir uçtan uca çözüm <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> doğrudan yazma deneyimini iş akışı içinde yükseltme özelliği.</span><span class="sxs-lookup"><span data-stu-id="ced3b-103">This sample provides an end-to-end solution that integrates the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature directly into the workflow authoring experience.</span></span> <span data-ttu-id="ced3b-104">Yapılandırma öğeleri, iş akışı etkinlikleri ve basitleştirin promosyon özelliğinin kullanımına iş akışı uzantıları koleksiyonu sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ced3b-104">A collection of configuration elements, workflow activities, and workflow extensions that simplify the use of the Promotion feature are provided.</span></span> <span data-ttu-id="ced3b-105">Ayrıca, bu koleksiyon kullanmayı gösteren basit bir iş akışı örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="ced3b-105">Additionally, the sample contains a simple workflow that demonstrates how to use this collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ced3b-106">Örnekler yalnızca eğitim amaçlı olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ced3b-106">Samples are provided for educational purposes only.</span></span> <span data-ttu-id="ced3b-107">Bunlar, bir üretim ortamı için tasarlanmamıştır ve bir üretim ortamında test edilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="ced3b-107">They are not intended for a production environment, and have not been tested in a production environment.</span></span> <span data-ttu-id="ced3b-108">Microsoft, bu örnekler için teknik destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="ced3b-108">Microsoft does not provide technical support for these samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ced3b-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ced3b-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="ced3b-110">Başlatılan bir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> veritabanı</span><span class="sxs-lookup"><span data-stu-id="ced3b-110">An initialized <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a><span data-ttu-id="ced3b-111">Örnek Proje</span><span class="sxs-lookup"><span data-stu-id="ced3b-111">Sample Projects</span></span>  
  
-   <span data-ttu-id="ced3b-112">**PropertyPromotionActivity** proje yükseltme özgü yapılandırma öğeleri, iş akışı etkinlikleri ve iş akışı uzantıları ilişkin dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="ced3b-112">The **PropertyPromotionActivity** project contains files pertaining to the promotion-specific configuration elements, workflow activities, and workflow extensions.</span></span>  
  
-   <span data-ttu-id="ced3b-113">**CounterServiceApplication** projesini içeren kullanan bir örnek iş akışı **SqlWorkflowInstanceStorePromotion** proje.</span><span class="sxs-lookup"><span data-stu-id="ced3b-113">The **CounterServiceApplication** project contains a sample workflow that uses the **SqlWorkflowInstanceStorePromotion** project.</span></span>  
  
-   <span data-ttu-id="ced3b-114">Karşı çalıştırılmalıdır SQL betiği (PropertyPromotionActivitySQLSample.sql) <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> veritabanı.</span><span class="sxs-lookup"><span data-stu-id="ced3b-114">A SQL script (PropertyPromotionActivitySQLSample.sql) that must be run against the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database.</span></span>  
  
-   <span data-ttu-id="ced3b-115">İki bağlantı bir çözüm dosyası [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projeleri (`PropertyPromotionActivity.sln`)</span><span class="sxs-lookup"><span data-stu-id="ced3b-115">A solution file that links the two [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projects (`PropertyPromotionActivity.sln`)</span></span>  
  
## <a name="to-set-up-and-run-the-sample"></a><span data-ttu-id="ced3b-116">Ayarlama ve çalıştırma örneği</span><span class="sxs-lookup"><span data-stu-id="ced3b-116">To set up and run the sample</span></span>  
  
1.  <span data-ttu-id="ced3b-117">Bir iş akışı Kalıcılık veritabanı başlatın.</span><span class="sxs-lookup"><span data-stu-id="ced3b-117">Initialize a workflow persistence database.</span></span>  
  
    1.  <span data-ttu-id="ced3b-118">Örnek dizine (\WF\Basic\Persistence\PropertyPromotionActivity) gidin ve CreateInstanceStore.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ced3b-118">Navigate to the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity) and run CreateInstanceStore.cmd.</span></span>  
  
    2.  <span data-ttu-id="ced3b-119">Yönetici ayrıcalıkları kullanılabilir durumda değilse, bir SQL Server oturumu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ced3b-119">If Administrator privileges are not available, create a SQL Server login.</span></span> <span data-ttu-id="ced3b-120">SQL Server Management Studio'da Git **güvenlik**, **oturumları**.</span><span class="sxs-lookup"><span data-stu-id="ced3b-120">In SQL Server Management Studio, go to **Security**, **Logins**.</span></span> <span data-ttu-id="ced3b-121">Sağ **oturumları** ve yeni bir oturum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ced3b-121">Right-click **Logins** and create a new login.</span></span> <span data-ttu-id="ced3b-122">Açarak SQL role ACL Kullanıcınızı eklemek **veritabanları**, **InstanceStore**, **güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="ced3b-122">Add your ACL user to the SQL role by opening **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="ced3b-123">Sağ **kullanıcılar** seçip **yeni kullanıcı**.</span><span class="sxs-lookup"><span data-stu-id="ced3b-123">Right-click **Users** and select **New user**.</span></span> <span data-ttu-id="ced3b-124">Ayarlama **oturum açma adı** yukarıda oluşturulan kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="ced3b-124">Set the **Login name** to the user created above.</span></span> <span data-ttu-id="ced3b-125">Kullanıcı için veritabanı rolü üyeliği System.Activities.DurableInstancing.InstanceStoreUsers (ve diğerleri) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ced3b-125">Add the user to the Database role membership System.Activities.DurableInstancing.InstanceStoreUsers (and others).</span></span> <span data-ttu-id="ced3b-126">Kullanıcı zaten (örneğin, dbo kullanıcısı) bulunmayabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ced3b-126">Note that the user might exist already (for example, user dbo).</span></span>  
  
2.  <span data-ttu-id="ced3b-127">PropertyPromotionActivity.sln çözüm dosyasını açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ced3b-127">Open the PropertyPromotionActivity.sln solution file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="ced3b-128">Yerel SQL Server Express yüklemesi dışında bir veritabanında örnek deposu oluşturduysanız, veritabanı bağlantı dizesini güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ced3b-128">If you created the instance store in a database other than a local installation of SQL Server Express, then you must update the database connection string.</span></span> <span data-ttu-id="ced3b-129">App.config dosyasını altında alter **CounterServiceApplication** değerini ayarlayarak `connectionString` özniteliği `sqlWorkflowInstanceStorePromotion` düğümü başlatıldı Kalıcılık veritabanına işaret eden, adım 1.</span><span class="sxs-lookup"><span data-stu-id="ced3b-129">Alter the App.config file under the **CounterServiceApplication** by setting the value of the `connectionString` attribute on the `sqlWorkflowInstanceStorePromotion` node so that it points to the persistence database that was initialized in step 1.</span></span>  
  
4.  <span data-ttu-id="ced3b-130">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ced3b-130">Build and run the solution.</span></span> <span data-ttu-id="ced3b-131">Bu sayaç WF hizmeti başlatın ve otomatik olarak bir iş akışı örneği başlatın.</span><span class="sxs-lookup"><span data-stu-id="ced3b-131">This will start the Counter WF service and automatically start a workflow instance.</span></span>  
  
5.  <span data-ttu-id="ced3b-132">Hızlı bir şekilde tüm satırları [dbo] seçin. (Bu görünüm 1. adımda CreateInstanceStore.cmd çalıştırarak eklendi) [counterService] görünümü Kalıcılık veritabanı.</span><span class="sxs-lookup"><span data-stu-id="ced3b-132">Quickly select all the rows in the [dbo].[CounterService] view in your persistence database (this view was added by running CreateInstanceStore.cmd in step 1).</span></span> <span data-ttu-id="ced3b-133">Ayarlama aşağıdakine benzer bir sonuç göreceksiniz:</span><span class="sxs-lookup"><span data-stu-id="ced3b-133">You will see a result set similar to the following:</span></span>  
  
    |<span data-ttu-id="ced3b-134">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ced3b-134">InstanceId</span></span>|<span data-ttu-id="ced3b-135">Ort</span><span class="sxs-lookup"><span data-stu-id="ced3b-135">CounterValue</span></span>|<span data-ttu-id="ced3b-136">CounterValueLastUpdated</span><span class="sxs-lookup"><span data-stu-id="ced3b-136">CounterValueLastUpdated</span></span>|  
    |----------------|------------------|-----------------------------|  
    |<span data-ttu-id="ced3b-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span><span class="sxs-lookup"><span data-stu-id="ced3b-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span></span>|<span data-ttu-id="ced3b-138">12</span><span class="sxs-lookup"><span data-stu-id="ced3b-138">12</span></span>|<span data-ttu-id="ced3b-139">2010-02-18 22:48:01.740</span><span class="sxs-lookup"><span data-stu-id="ced3b-139">2010-02-18 22:48:01.740</span></span>|  
  
     <span data-ttu-id="ced3b-140">Görünümü yenileniyor tutmak gibi her iki saniye Ort ve CounterValueLastUpdated değiştirme fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ced3b-140">As you keep refreshing the view, you will notice that CounterValue and CounterValueLastUpdated change every two seconds.</span></span> <span data-ttu-id="ced3b-141">Bu sayaç kendisini güncelleştirir aralığıdır.</span><span class="sxs-lookup"><span data-stu-id="ced3b-141">This is the interval at which the counter updates itself.</span></span> <span data-ttu-id="ced3b-142">Ort ve CounterValueLastUpdated bu iş akışı için yükseltilen özellikleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ced3b-142">CounterValue and CounterValueLastUpdated represent promoted properties for this workflow.</span></span>  
  
## <a name="to-remove-the-sample"></a><span data-ttu-id="ced3b-143">Örnek kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="ced3b-143">To remove the sample</span></span>  
  
-   <span data-ttu-id="ced3b-144">RemoveInstanceStore.cmd örnek dizinde (\WF\Basic\Persistence\PropertyPromotionActivity) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ced3b-144">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity).</span></span>  
  
## <a name="understanding-this-sample"></a><span data-ttu-id="ced3b-145">Bu örnek anlama</span><span class="sxs-lookup"><span data-stu-id="ced3b-145">Understanding This Sample</span></span>  
 <span data-ttu-id="ced3b-146">Örnek, iki proje dosyası ve SQL içerir:</span><span class="sxs-lookup"><span data-stu-id="ced3b-146">The sample contains two projects and an SQL file:</span></span>  
  
-   <span data-ttu-id="ced3b-147">**CounterServiceApplication** basit bir sayaç WF hizmetini barındıran bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ced3b-147">**CounterServiceApplication** is a console application that hosts a simple Counter WF service.</span></span> <span data-ttu-id="ced3b-148">Bir tek yönlü mesaj aracılığıyla bağlı `Start` uç noktası, iş akışı sayısı 0'dan bir sayaç değişkeni her iki saniye artan 29 için.</span><span class="sxs-lookup"><span data-stu-id="ced3b-148">Upon receiving a one-way message through the `Start` endpoint, the workflow counts from 0 to 29, incrementing a counter variable every two seconds.</span></span> <span data-ttu-id="ced3b-149">Her sayacı artırma sonra iş akışı devam ediyorsa ve yükseltilen özellikleri [dbo] güncelleştirilir. [CounterService] görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="ced3b-149">After every counter increment, the workflow persists, and the promoted properties are updated in the [dbo].[CounterService] view.</span></span> <span data-ttu-id="ced3b-150">Konsol uygulamasını çalıştırdığınızda, WF hizmetini barındıran ve bir ileti gönderir `Start` uç noktası, bir sayaç WF örneği oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ced3b-150">When the console application is run, it hosts the WF service and sends a message to the `Start` endpoint, creating a Counter WF instance.</span></span>  
  
-   <span data-ttu-id="ced3b-151">**PropertyPromotionActivity** yapılandırma öğeleri, iş akışı etkinlikleri ve iş akışı uzantıların bulunduğu bir sınıf kitaplığı, **CounterServiceApplication** kullanır.</span><span class="sxs-lookup"><span data-stu-id="ced3b-151">**PropertyPromotionActivity** is a class library that contains the configuration elements, workflow activities, and workflow extensions that the **CounterServiceApplication** uses.</span></span>  
  
-   <span data-ttu-id="ced3b-152">**PropertyPromotionActivitySQLSample.sql** oluşturur ve ekler görünümü [dbo]. [ Veritabanına counterService].</span><span class="sxs-lookup"><span data-stu-id="ced3b-152">**PropertyPromotionActivitySQLSample.sql** creates and adds the view [dbo].[CounterService] to the database.</span></span>  
  
### <a name="counterserviceapplication"></a><span data-ttu-id="ced3b-153">CounterServiceApplication</span><span class="sxs-lookup"><span data-stu-id="ced3b-153">CounterServiceApplication</span></span>  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a><span data-ttu-id="ced3b-154">SqlWorkflowInstanceStorePromotion yapılandırma öğesini kullanarak</span><span class="sxs-lookup"><span data-stu-id="ced3b-154">Using the SqlWorkflowInstanceStorePromotion Configuration Element</span></span>  
 <span data-ttu-id="ced3b-155">`SqlWorkflowInstanceStorePromotion` Yapılandırma öğesi devraldığı `SqlWorkflowInstanceStore` yapılandırma öğesi, ancak adlı bir ek yapılandırma öğesi ekler `promotionSets`.</span><span class="sxs-lookup"><span data-stu-id="ced3b-155">The `SqlWorkflowInstanceStorePromotion` configuration element inherits from the `SqlWorkflowInstanceStore` configuration element, but adds an additional configuration element called `promotionSets`.</span></span> <span data-ttu-id="ced3b-156">`promotionSets` Öğesi yapılandırması yükseltilen özelliklerinden belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ced3b-156">The `promotionSets` element enables the user to specify promoted properties through configuration.</span></span> <span data-ttu-id="ced3b-157">Bu örnek tarafından kullanılan yapılandırma dosyasıdır:</span><span class="sxs-lookup"><span data-stu-id="ced3b-157">This is the configuration file that is used by the sample:</span></span>  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 <span data-ttu-id="ced3b-158">[Dbo] tanımını inceleyin. [CounterService] görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="ced3b-158">Examine the definition for the [dbo].[CounterService] view.</span></span>  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 <span data-ttu-id="ced3b-159">Bir iş akışı örneği devam ederse, bir satır içine eklenir `InstancePromotedProperties` görüntülemek için her `PromotionSet` yapılandırmasında tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="ced3b-159">When a workflow instance persists, a row is inserted into the `InstancePromotedProperties` view for each `PromotionSet` defined in the configuration.</span></span> <span data-ttu-id="ced3b-160">Bu satır yükseltilen tüm özelliklerini içerir `PromotionSet` (bir yükseltilen özellik sütun başına).</span><span class="sxs-lookup"><span data-stu-id="ced3b-160">This row contains all the promoted properties of the `PromotionSet` (one promoted property per column).</span></span> <span data-ttu-id="ced3b-161">Bu `PromotionSet` tanımlama grubu tarafından Anahtarlanan: `InstanceId, PromotionName`.</span><span class="sxs-lookup"><span data-stu-id="ced3b-161">This `PromotionSet` is keyed by the tuple: `InstanceId, PromotionName`.</span></span> <span data-ttu-id="ced3b-162">Bu örnekte, bir sahip olduğumuz `PromotionSet` olan adı özniteliği yapılandırmasında tanımlı `CounterService`.</span><span class="sxs-lookup"><span data-stu-id="ced3b-162">In this sample, we have one `PromotionSet` defined in configuration whose name attribute is `CounterService`.</span></span> <span data-ttu-id="ced3b-163">Not nasıl `PromotionName` öğesinin ad özniteliği için sütun değeri eşittir `PromotionSet` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ced3b-163">Note how the `PromotionName` column value is equal to the name attribute of the `PromotionSet` element.</span></span>  
  
 <span data-ttu-id="ced3b-164">Sırasını `promotedValue` öğeleri karşılık gelen yükseltilen özelliklerinde yerleşimini ile `InstancePromotedProperties` görünümü.</span><span class="sxs-lookup"><span data-stu-id="ced3b-164">The order of the `promotedValue` elements correlates with the placement of the promoted properties in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="ced3b-165">`Count` İlk `promotedValue` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ced3b-165">`Count` is the first `promotedValue` element.</span></span> <span data-ttu-id="ced3b-166">Sonuç olarak, eşlenmiş `Value1` sütununda `InstancePromotedProperties` görünümü.</span><span class="sxs-lookup"><span data-stu-id="ced3b-166">As a result, it is mapped to the `Value1` column in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="ced3b-167">`LastIncrementedAt` İkinci `promotedValue` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ced3b-167">`LastIncrementedAt` is the second `promotedValue` element.</span></span> <span data-ttu-id="ced3b-168">Sonuç olarak, eşlenmiş `Value2` sütununda `InstancePromotedProperties` görünümü.</span><span class="sxs-lookup"><span data-stu-id="ced3b-168">As a result, it is mapped to the `Value2` column in the `InstancePromotedProperties` view.</span></span>  
  
#### <a name="using-the-promotevalue-activity"></a><span data-ttu-id="ced3b-169">PromoteValue etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="ced3b-169">Using the PromoteValue Activity</span></span>  
 <span data-ttu-id="ced3b-170">Windows Workflow Foundation Designer CounterService.xamlx dosyasını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="ced3b-170">Examine the CounterService.xamlx file in the Windows Workflow Foundation Designer.</span></span> <span data-ttu-id="ced3b-171">WF tanımında iki özel etkinliği olduğuna dikkat edin: `PromoteValue<DateTime>` ve `PromoteValue<Int32>`.</span><span class="sxs-lookup"><span data-stu-id="ced3b-171">Notice that there are two special activities in the WF definition: `PromoteValue<DateTime>` and `PromoteValue<Int32>`.</span></span>  
  
 <span data-ttu-id="ced3b-172">`PromoteValue<Int32>` Etkinliğinde, `Name` üye olarak tanımlanan `Count`.</span><span class="sxs-lookup"><span data-stu-id="ced3b-172">The `PromoteValue<Int32>` activity has its `Name` member defined as `Count`.</span></span> <span data-ttu-id="ced3b-173">Bu ilk eşleşen `promotedValue` yapılandırma öğesi ve kendi `Value` olarak tanımlanan `Counter` iş akışı değişkeni.</span><span class="sxs-lookup"><span data-stu-id="ced3b-173">This matches with the first `promotedValue` element in the configuration, and has its `Value` defined as the `Counter` workflow variable.</span></span> <span data-ttu-id="ced3b-174">İş akışı devam ederse, `Counter` iş akışı değişkeninin yükseltilen bir özellikte olarak kalıcıdır `Value1` sütununun `InstancePromotedProperties` görünümü.</span><span class="sxs-lookup"><span data-stu-id="ced3b-174">When the workflow persists, the `Counter` workflow variable is persisted as a promoted property into the `Value1` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="ced3b-175">`PromoteValue<DateTime>` Etkinliğinde, `Name` üye olarak tanımlanan `LastIncrementedAt`.</span><span class="sxs-lookup"><span data-stu-id="ced3b-175">The `PromoteValue<DateTime>` activity has its `Name` member defined as `LastIncrementedAt`.</span></span> <span data-ttu-id="ced3b-176">Bu ikinci ile eşleşen `promotedValue` yapılandırma öğesi ve kendi `Value` olarak tanımlanan `TimeLastIncremented` iş akışı değişkeni.</span><span class="sxs-lookup"><span data-stu-id="ced3b-176">This matches with the second `promotedValue` element in the configuration, and has its `Value` defined as the `TimeLastIncremented` workflow variable.</span></span> <span data-ttu-id="ced3b-177">Bunun anlamı, değerini iş akışı devam ederse `TimeLastIncremented` iş akışı değişkeni kalıcı olarak yükseltilen bir özellikte `Value2` sütununun `InstancePromotedProperties` görünümü.</span><span class="sxs-lookup"><span data-stu-id="ced3b-177">This means that when the workflow persists, the value for the `TimeLastIncremented` workflow variable will be persisted as a promoted property into the `Value2` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="ced3b-178">Unutmayın `PromotedValue` ayrıca etkinliğinde adlı bir Boolean üye `ClearExistingPromotedData`.</span><span class="sxs-lookup"><span data-stu-id="ced3b-178">Note that the `PromotedValue` activity also has a Boolean member called `ClearExistingPromotedData`.</span></span> <span data-ttu-id="ced3b-179">Bu üye ayarlandığında `true`, bu iş akışında o noktaya kadar tüm yükseltilen özellik değerleri temizler.</span><span class="sxs-lookup"><span data-stu-id="ced3b-179">When this member is set to `true`, this clears all the promoted property values up to that point in the workflow.</span></span> <span data-ttu-id="ced3b-180">Örneğin, bir sıralama etkinliği olarak tanımlanması durumunda aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ced3b-180">For example, if a Sequence activity is defined as follows:</span></span>  
  
1.  <span data-ttu-id="ced3b-181">PromoteValue {adı "Count", değer = 3 =}</span><span class="sxs-lookup"><span data-stu-id="ced3b-181">PromoteValue { Name = "Count", Value = 3}</span></span>  
  
2.  <span data-ttu-id="ced3b-182">PromoteValue {adı "LastIncrementedAt", değer = 1-1-2000 =}</span><span class="sxs-lookup"><span data-stu-id="ced3b-182">PromoteValue {Name = "LastIncrementedAt", Value = 1-1-2000 }</span></span>  
  
3.  <span data-ttu-id="ced3b-183">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="ced3b-183">Persist</span></span>  
  
4.  <span data-ttu-id="ced3b-184">PromoteValue {adı "Count", değer = 4, ClearExistingPromotedData = true =}</span><span class="sxs-lookup"><span data-stu-id="ced3b-184">PromoteValue {Name = "Count", Value = 4, ClearExistingPromotedData = true}</span></span>  
  
5.  <span data-ttu-id="ced3b-185">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="ced3b-185">Persist</span></span>  
  
 <span data-ttu-id="ced3b-186">Yükseltilen değeri ikinci devam ettir üzerinde `Count` 4 olur.</span><span class="sxs-lookup"><span data-stu-id="ced3b-186">On the second persist, the promoted value for `Count` will be 4.</span></span> <span data-ttu-id="ced3b-187">Ancak, yükseltilen değeri `LastIncrementedAt` olacaktır `NULL`.</span><span class="sxs-lookup"><span data-stu-id="ced3b-187">However, the promoted value for `LastIncrementedAt` will be `NULL`.</span></span> <span data-ttu-id="ced3b-188">Varsa `ClearExistingPromotedData` ayarlanmadı `true` 4. adımda, ardından ikinci devam ettir sonra yükseltilen sayısı değeri 4 olur.</span><span class="sxs-lookup"><span data-stu-id="ced3b-188">If `ClearExistingPromotedData` was not set to `true` for step 4, then after the second persist, the promoted value for Count would be 4.</span></span> <span data-ttu-id="ced3b-189">Sonuç olarak, yükseltilen değeri `LastIncrementedAt` 1-1-2000 olmaya.</span><span class="sxs-lookup"><span data-stu-id="ced3b-189">As a result, the promoted value for `LastIncrementedAt` would still be 1-1-2000.</span></span>  
  
### <a name="propertypromotionactivity"></a><span data-ttu-id="ced3b-190">PropertyPromotionActivity</span><span class="sxs-lookup"><span data-stu-id="ced3b-190">PropertyPromotionActivity</span></span>  
 <span data-ttu-id="ced3b-191">Bu sınıf kitaplığı kullanımını kolaylaştırmak için aşağıdaki genel sınıfları içeren <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> yükseltme özelliği.</span><span class="sxs-lookup"><span data-stu-id="ced3b-191">This class library contains the following public classes to simplify use of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature.</span></span>  
  
#### <a name="promotevalue-class"></a><span data-ttu-id="ced3b-192">PromoteValue sınıfı</span><span class="sxs-lookup"><span data-stu-id="ced3b-192">PromoteValue Class</span></span>  
 <span data-ttu-id="ced3b-193">Bu sınıf, bir özellik yükseltir.</span><span class="sxs-lookup"><span data-stu-id="ced3b-193">This class promotes one property.</span></span> <span data-ttu-id="ced3b-194">Yükseltilen özellik adını bir ad özniteliği eşleşmelidir bir `promotedValue` yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ced3b-194">The name of the promoted property should match a name attribute of a `promotedValue` element in the configuration.</span></span> <span data-ttu-id="ced3b-195">Bu etkinlik iş akışı Tasarımcısı'nda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ced3b-195">This activity can be used in the Workflow Designer.</span></span> <span data-ttu-id="ced3b-196">CounterServiceApplication kullanım örneği için bkz.</span><span class="sxs-lookup"><span data-stu-id="ced3b-196">See the CounterServiceApplication for an example usage.</span></span>  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 <span data-ttu-id="ced3b-197">ClearExistingPromotedData (Boole)</span><span class="sxs-lookup"><span data-stu-id="ced3b-197">ClearExistingPromotedData (Bool)</span></span>  
 <span data-ttu-id="ced3b-198">Bu etkinlik önce yükseltilen tüm değerleri temizler.</span><span class="sxs-lookup"><span data-stu-id="ced3b-198">Clears all values that were promoted before this activity.</span></span>  
  
 <span data-ttu-id="ced3b-199">Adı (dize)</span><span class="sxs-lookup"><span data-stu-id="ced3b-199">Name (string)</span></span>  
 <span data-ttu-id="ced3b-200">Bu özellik temsil eden adı.</span><span class="sxs-lookup"><span data-stu-id="ced3b-200">The name that represents this property.</span></span> <span data-ttu-id="ced3b-201">Bu ad özniteliği eşleşmelidir bir \<promotedValue > yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ced3b-201">This should match the name attribute of a \<promotedValue> element in the configuration.</span></span>  
  
 <span data-ttu-id="ced3b-202">Değer (InArgument\<T >)</span><span class="sxs-lookup"><span data-stu-id="ced3b-202">Value (InArgument\<T>)</span></span>  
 <span data-ttu-id="ced3b-203">Değişken / Sütun saklamak istediğiniz değer.</span><span class="sxs-lookup"><span data-stu-id="ced3b-203">The variable / value that you want to store in the column.</span></span>  
  
#### <a name="promotevalues-class"></a><span data-ttu-id="ced3b-204">PromoteValues sınıfı</span><span class="sxs-lookup"><span data-stu-id="ced3b-204">PromoteValues Class</span></span>  
 <span data-ttu-id="ced3b-205">Birden çok özellik yükseltir.</span><span class="sxs-lookup"><span data-stu-id="ced3b-205">Promotes multiple properties.</span></span> <span data-ttu-id="ced3b-206">Yükseltilen özellik adlarının tüm adı öznitelikler eşleşmelidir `promotedValue` yapılandırma öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ced3b-206">The names of the promoted properties should match all name attributes in the `promotedValue` elements in the configuration.</span></span> <span data-ttu-id="ced3b-207">Kullanım benzer `PromoteValue` aynı anda birden çok özellik yükseltilebilir olgu dışında bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ced3b-207">Usage is similar to the `PromoteValue` activity, except for the fact that multiple properties can be promoted at the same time.</span></span> <span data-ttu-id="ced3b-208">Bu etkinlik iş akışı Tasarımcısı'nda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ced3b-208">This activity cannot be used in the Workflow Designer.</span></span>  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a><span data-ttu-id="ced3b-209">SqlWorkflowInstanceStorePromotionBehavior</span><span class="sxs-lookup"><span data-stu-id="ced3b-209">SqlWorkflowInstanceStorePromotionBehavior</span></span>  
 <span data-ttu-id="ced3b-210">Öğesinden türetilen `SqlWorkflowInstanceStoreBehavior`.</span><span class="sxs-lookup"><span data-stu-id="ced3b-210">Derives from `SqlWorkflowInstanceStoreBehavior`.</span></span> <span data-ttu-id="ced3b-211">Bu türetilmiş sınıf özel Kalıcılık Katılımcısı (Ayrıca bu kitaplık bir parçası) bir iş akışı uzantısı ekler.</span><span class="sxs-lookup"><span data-stu-id="ced3b-211">This derived class adds a custom persistence participant (also a part of this library) as a workflow extension.</span></span> <span data-ttu-id="ced3b-212">Önceki iki iş akışı etkinlikleri uygulanması, bu özel Kalıcılık Katılımcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ced3b-212">The implementation of the previous two workflow activities relies on this custom persistence participant.</span></span>  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 <span data-ttu-id="ced3b-213">Bu sınıf kitaplığını da içeren `ConfigurationElement` logrequest olayını `SqlWorkflowInstanceStorePromotionElement` ve önceki yükseltme etkinlikleri tarafından kullanılan özel Kalıcılık Katılımcısı.</span><span class="sxs-lookup"><span data-stu-id="ced3b-213">This class library also contains the `ConfigurationElement` implementation for the `SqlWorkflowInstanceStorePromotionElement` and a custom persistence participant used by the previous promotion activities.</span></span>  
  
### <a name="propertypromotionactivitysqlsample"></a><span data-ttu-id="ced3b-214">PropertyPromotionActivitySQLSample</span><span class="sxs-lookup"><span data-stu-id="ced3b-214">PropertyPromotionActivitySQLSample</span></span>  
 <span data-ttu-id="ced3b-215">Bu SQL dosyası oluşturur bir `[dbo].[CounterService]` ek olarak görüntülemek `[InstancePromotedProperties]` CounterService yükseltme kümesine sahip tüm örneklerini sorgulamak için görünümü.</span><span class="sxs-lookup"><span data-stu-id="ced3b-215">This SQL file creates a `[dbo].[CounterService]` view in addition to the `[InstancePromotedProperties]` view for querying all instances that have a CounterService Promotion set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ced3b-216">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="ced3b-216">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ced3b-217">Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:</span><span class="sxs-lookup"><span data-stu-id="ced3b-217">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ced3b-218">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ced3b-218">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ced3b-219">Bu örnek, şu dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="ced3b-219">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a><span data-ttu-id="ced3b-220">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ced3b-220">See Also</span></span>  
 [<span data-ttu-id="ced3b-221">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="ced3b-221">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
