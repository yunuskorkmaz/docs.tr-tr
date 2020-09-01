---
title: Veri kümesi ve DataTable Güvenlik Kılavuzu
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: 4fe8a062c762cc70d33243e3443aa9bf55635f98
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137623"
---
# <a name="dataset-and-datatable-security-guidance"></a><span data-ttu-id="30677-102">Veri kümesi ve DataTable Güvenlik Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="30677-102">DataSet and DataTable security guidance</span></span>

<span data-ttu-id="30677-103">Bu makale için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="30677-103">This article applies to:</span></span>

* <span data-ttu-id="30677-104">.NET Framework (tüm sürümler)</span><span class="sxs-lookup"><span data-stu-id="30677-104">.NET Framework (all versions)</span></span>
* <span data-ttu-id="30677-105">.NET Core ve üzeri</span><span class="sxs-lookup"><span data-stu-id="30677-105">.NET Core and later</span></span>
* <span data-ttu-id="30677-106">.NET 5,0 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="30677-106">.NET 5.0 and later</span></span>

<span data-ttu-id="30677-107">[DataSet](/dotnet/api/system.data.dataset) ve [DataTable](/dotnet/api/system.data.datatable) türleri, veri kümelerinin yönetilen nesneler olarak belirtilmesine izin veren eski .net bileşenleridir.</span><span class="sxs-lookup"><span data-stu-id="30677-107">The [DataSet](/dotnet/api/system.data.dataset) and [DataTable](/dotnet/api/system.data.datatable) types are legacy .NET components that allow representing data sets as managed objects.</span></span> <span data-ttu-id="30677-108">Bu bileşenler, .NET 1,0 ' de özgün [ADO.NET altyapısının](/dotnet/framework/data/adonet/dataset-datatable-dataview/)bir parçası olarak sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="30677-108">These components were introduced in .NET 1.0 as part of the original [ADO.NET infrastructure](/dotnet/framework/data/adonet/dataset-datatable-dataview/).</span></span> <span data-ttu-id="30677-109">Bu kullanıcıların, ilişkisel veri kümesi üzerinde yönetilen bir görünüm sağlaması, verilerin temel kaynağının XML, SQL veya başka bir teknoloji olması durumunda olup olmadığını soyutlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="30677-109">Their goal was to provide a managed view over a relational data set, abstracting away whether the underlying source of the data was XML, SQL, or another technology.</span></span>

<span data-ttu-id="30677-110">ADO.NET hakkında daha fazla bilgi için, bkz. [ADO.net belgeleri](/dotnet/framework/data/adonet/).</span><span class="sxs-lookup"><span data-stu-id="30677-110">For more information on ADO.NET, including more modern data view paradigms, see [the ADO.NET documentation](/dotnet/framework/data/adonet/).</span></span>

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a><span data-ttu-id="30677-111">XML 'den bir veri kümesi veya DataTable serisi kaldırılırken varsayılan kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="30677-111">Default restrictions when deserializing a DataSet or DataTable from XML</span></span>

<span data-ttu-id="30677-112">.NET Framework, .NET Core ve .NET ' in tüm desteklenen sürümlerinde, `DataSet` `DataTable` Serisi kaldırılan verilerde bulunabilecek nesne türleri için aşağıdaki kısıtlamaları yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="30677-112">On all supported versions of .NET Framework, .NET Core, and .NET, `DataSet` and `DataTable` place the following restrictions on what types of objects may be present in the deserialized data.</span></span> <span data-ttu-id="30677-113">Varsayılan olarak, bu liste şu şekilde kısıtlanır:</span><span class="sxs-lookup"><span data-stu-id="30677-113">By default, this list is restricted to:</span></span>

* <span data-ttu-id="30677-114">Temel elemanlar ve ilkel eşdeğerleri: `bool` , `char` ,, `sbyte` `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` , `float` , `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` `SqlString` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,</span><span class="sxs-lookup"><span data-stu-id="30677-114">Primitives and primitive equivalents: `bool`, `char`, `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `DateTime`, `DateTimeOffset`, `TimeSpan`, `string`, `Guid`, `SqlBinary`, `SqlBoolean`, `SqlByte`, `SqlBytes`, `SqlChars`, `SqlDateTime`, `SqlDecimal`, `SqlDouble`, `SqlGuid`, `SqlInt16`, `SqlInt32`, `SqlInt64`, `SqlMoney`, `SqlSingle`, and `SqlString`.</span></span>
* <span data-ttu-id="30677-115">Yaygın olarak kullanılan temel olmayan: `Type` , `Uri` , ve `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="30677-115">Commonly used non-primitives: `Type`, `Uri`, and `BigInteger`.</span></span>
* <span data-ttu-id="30677-116">Yaygın olarak kullanılan _System. Drawing_ türleri: `Color` ,,, `Point` `PointF` `Rectangle` , `RectangleF` , `Size` , ve `SizeF` .</span><span class="sxs-lookup"><span data-stu-id="30677-116">Commonly used _System.Drawing_ types: `Color`, `Point`, `PointF`, `Rectangle`, `RectangleF`, `Size`, and `SizeF`.</span></span>
* <span data-ttu-id="30677-117">`Enum` türü.</span><span class="sxs-lookup"><span data-stu-id="30677-117">`Enum` types.</span></span>
* <span data-ttu-id="30677-118">Yukarıdaki türlerin dizileri ve listeleri.</span><span class="sxs-lookup"><span data-stu-id="30677-118">Arrays and lists of the above types.</span></span>

<span data-ttu-id="30677-119">Gelen XML verileri, türü bu listede olmayan bir nesne içeriyorsa:</span><span class="sxs-lookup"><span data-stu-id="30677-119">If the incoming XML data contains an object whose type is not in this list:</span></span>

* <span data-ttu-id="30677-120">Aşağıdaki ileti ve yığın izleme ile bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="30677-120">An exception is thrown with the following message and stack trace.</span></span>  
<span data-ttu-id="30677-121">Hata İletisi:</span><span class="sxs-lookup"><span data-stu-id="30677-121">Error Message:</span></span>  
<span data-ttu-id="30677-122">Burada System. InvalidOperationException: Type ' \<Type Name\> , Version = \<n.n.n.n\> , Culture = \<culture\> , PublicKeyToken = ' kullanılamaz \<token value\> .</span><span class="sxs-lookup"><span data-stu-id="30677-122">System.InvalidOperationException : Type '\<Type Name\>, Version=\<n.n.n.n\>, Culture=\<culture\>, PublicKeyToken=\<token value\>' is not allowed here.</span></span> <span data-ttu-id="30677-123">[https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227)Daha fazla ayrıntı için bkz..</span><span class="sxs-lookup"><span data-stu-id="30677-123">See [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227) for more details.</span></span>  
<span data-ttu-id="30677-124">Yığın Izlemesi:</span><span class="sxs-lookup"><span data-stu-id="30677-124">Stack Trace:</span></span>  
<span data-ttu-id="30677-125">System. Data. TypeLimiter. EnsureTypeIsAllowed (tür türü, TypeLimiter capturedLimiter) konumunda</span><span class="sxs-lookup"><span data-stu-id="30677-125">at System.Data.TypeLimiter.EnsureTypeIsAllowed(Type type, TypeLimiter capturedLimiter)</span></span>  
<span data-ttu-id="30677-126">System. Data. DataColumn. UpdateColumnType (tür türü, StorageType typeCode) konumunda</span><span class="sxs-lookup"><span data-stu-id="30677-126">at System.Data.DataColumn.UpdateColumnType(Type type, StorageType typeCode)</span></span>  
<span data-ttu-id="30677-127">System. Data. DataColumn. set_DataType (tür değeri)</span><span class="sxs-lookup"><span data-stu-id="30677-127">at System.Data.DataColumn.set_DataType(Type value)</span></span>  

* <span data-ttu-id="30677-128">Seri durumdan çıkarma işlemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="30677-128">The deserialization operation fails.</span></span>

<span data-ttu-id="30677-129">XML 'i var olan bir `DataSet` veya `DataTable` örneğe yüklerken, var olan sütun tanımları da hesaba alınır.</span><span class="sxs-lookup"><span data-stu-id="30677-129">When loading XML into an existing `DataSet` or `DataTable` instance, the existing column definitions are also taken into account.</span></span> <span data-ttu-id="30677-130">Tablo, özel bir türün sütun tanımını zaten içeriyorsa, bu tür XML serisini kaldırma işleminin süresi için izin verilenler listesine geçici olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="30677-130">If the table already contains a column definition of a custom type, that type is temporarily added to the allow list for the duration of the XML deserialization operation.</span></span>

> [!NOTE]
> <span data-ttu-id="30677-131">Bir öğesine sütun eklediğinizde `DataTable` , `ReadXml` XML 'den şemayı okumaz ve şema onunla eşleşmezse, bu yöntemi kullanmak için tüm sütunları kendiniz eklemeniz gerekir, bu nedenle, bu yöntemi kullanmak için tüm sütunları eklemeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="30677-131">Once you add columns to a `DataTable`, `ReadXml` will not read the schema from the XML, and if the schema does not match it will also not read in the records, so you will need to add all the columns yourself to use this method.</span></span>

```cs
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

<span data-ttu-id="30677-132">Nesne türü kısıtlamaları, `XmlSerializer` veya örneğinin serisini kaldırmak için kullanılırken de geçerlidir `DataSet` `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="30677-132">The object type restrictions also apply when using `XmlSerializer` to deserialize an instance of `DataSet` or `DataTable`.</span></span> <span data-ttu-id="30677-133">Ancak, `BinaryFormatter` veya örneğinin serisini kaldırmak için kullanılırken uygulanamazlar `DataSet` `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="30677-133">However, they may not apply when using `BinaryFormatter` to deserialize an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="30677-134">`DataAdapter.Fill`Bir `DataTable` ÖRNEĞIN, xml serisini kaldırma API 'leri kullanılmadan doğrudan bir veritabanından doldurulduğu gibi, nesne türü kısıtlamaları kullanırken uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="30677-134">The object type restrictions don't apply when using `DataAdapter.Fill`, such as when a `DataTable` instance is populated directly from a database without using the XML deserialization APIs.</span></span>

### <a name="extend-the-list-of-allowed-types"></a><span data-ttu-id="30677-135">İzin verilen türlerin listesini genişletme</span><span class="sxs-lookup"><span data-stu-id="30677-135">Extend the list of allowed types</span></span>

<span data-ttu-id="30677-136">Bir uygulama, yukarıda listelenen yerleşik türlere ek olarak, izin verilen türler listesini özel türleri içerecek şekilde genişletebilir.</span><span class="sxs-lookup"><span data-stu-id="30677-136">An app can extend the allowed types list to include custom types in addition to the built-in types listed above.</span></span> <span data-ttu-id="30677-137">İzin verilen türler listesini genişlediğinde, değişiklik uygulamadaki _Tüm_ `DataSet` ve `DataTable` örnekleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="30677-137">If extending the allowed types list, the change affects _all_ `DataSet` and `DataTable` instances within the app.</span></span> <span data-ttu-id="30677-138">Türler, yerleşik izin verilen türler listesinden kaldırılamaz.</span><span class="sxs-lookup"><span data-stu-id="30677-138">Types cannot be removed from the built-in allowed types list.</span></span>

#### <a name="extend-through-configuration-net-framework-40---48"></a><span data-ttu-id="30677-139">Yapılandırma ile genişletme (.NET Framework 4,0-4,8)</span><span class="sxs-lookup"><span data-stu-id="30677-139">Extend through configuration (.NET Framework 4.0 - 4.8)</span></span>

<span data-ttu-id="30677-140">_App.config_ , izin verilen türler listesini genişletmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-140">_App.config_ can be used to extend the allowed types list.</span></span> <span data-ttu-id="30677-141">İzin verilen türler listesini genişletmek için:</span><span class="sxs-lookup"><span data-stu-id="30677-141">To extend the allowed types list:</span></span>

* <span data-ttu-id="30677-142">`<configSections>` _System. Data_ yapılandırma bölümüne bir başvuru eklemek için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="30677-142">Use the `<configSections>` element to add a reference to the _System.Data_ configuration section.</span></span>
* <span data-ttu-id="30677-143">`<system.data.dataset.serialization>` / `<allowedTypes>` Ek türleri belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="30677-143">Use `<system.data.dataset.serialization>`/`<allowedTypes>` to specify additional types.</span></span>

<span data-ttu-id="30677-144">Her `<add>` öğe, kendi derleme nitelikli tür adını kullanarak yalnızca bir tür belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="30677-144">Each `<add>` element must specify only one type by using its assembly qualified type name.</span></span> <span data-ttu-id="30677-145">İzin verilen türler listesine ek türler eklemek için, birden çok `<add>` öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="30677-145">To add additional types to the allowed types list, use multiple `<add>` elements.</span></span>

<span data-ttu-id="30677-146">Aşağıdaki örnek, özel tür ekleyerek izin verilen türlerin listesini genişletmeyi gösterir `Fabrikam.CustomType` .</span><span class="sxs-lookup"><span data-stu-id="30677-146">The following sample shows extending the allowed types list by adding the custom type `Fabrikam.CustomType`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="30677-147">Bir türün derleme nitelikli adını almak için, aşağıdaki kodda gösterildiği gibi [Type. AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="30677-147">To retrieve the assembly qualified name of a type, use the [Type.AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) property, as demonstrated in the following code.</span></span>

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a><span data-ttu-id="30677-148">Yapılandırma ile genişletme (.NET Framework 2,0-3,5)</span><span class="sxs-lookup"><span data-stu-id="30677-148">Extend through configuration (.NET Framework 2.0 - 3.5)</span></span>

<span data-ttu-id="30677-149">Uygulamanız 2,0 veya 3,5 .NET Framework hedefliyorsa, izin verilen türler listesini genişletmek için yukarıdaki _App.config_ mekanizmasını kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30677-149">If your app targets .NET Framework 2.0 or 3.5, you can still use the above _App.config_ mechanism to extend the allowed types list.</span></span> <span data-ttu-id="30677-150">Ancak, `<configSections>` aşağıdaki kodda gösterildiği gibi, öğesi biraz farklı görünecektir:</span><span class="sxs-lookup"><span data-stu-id="30677-150">However, your `<configSections>` element will look slightly different, as shown in the following code:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a><span data-ttu-id="30677-151">Programlı olarak genişlet (.NET Framework, .NET Core, .NET 5.0 +)</span><span class="sxs-lookup"><span data-stu-id="30677-151">Extend programmatically (.NET Framework, .NET Core, .NET 5.0+)</span></span>

<span data-ttu-id="30677-152">İzin verilen türlerin listesi Ayrıca, aşağıdaki kodda gösterildiği gibi, iyi bilinen Key _System. Data. Datasetdefaultallodilimlerin Types_ile [AppDomain. SetData](/dotnet/api/system.appdomain.setdata) kullanılarak programlı bir şekilde genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="30677-152">The list of allowed types can also be extended programmatically by using [AppDomain.SetData](/dotnet/api/system.appdomain.setdata) with the well-known key _System.Data.DataSetDefaultAllowedTypes_, as shown in the following code.</span></span>

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

<span data-ttu-id="30677-153">Uzantı mekanizması kullanılıyorsa, Key _System. Data. Datasetdefaultallodilimlerin Types_ ile ilişkili değer türünde olmalıdır `Type[]` .</span><span class="sxs-lookup"><span data-stu-id="30677-153">If using the extension mechanism, the value associated with the key _System.Data.DataSetDefaultAllowedTypes_ must be of type `Type[]`.</span></span>

<span data-ttu-id="30677-154">.NET Framework, izin verilen türlerin listesi hem _App.config_ hem de ile genişletilebilir `AppDomain.SetData` .</span><span class="sxs-lookup"><span data-stu-id="30677-154">On .NET Framework, the list of allowed types may be extended both with _App.config_ and `AppDomain.SetData`.</span></span> <span data-ttu-id="30677-155">Bu durumda, `DataSet` `DataTable` türü her iki listede de varsa, bir nesnenin veri parçası olarak seri durumdan çıkmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="30677-155">In this case, `DataSet` and `DataTable` will allow an object to be deserialized as part of the data if its type is present in either list.</span></span>

### <a name="run-an-app-in-audit-mode-net-framework"></a><span data-ttu-id="30677-156">Bir uygulamayı denetim modunda çalıştırma (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="30677-156">Run an app in audit mode (.NET Framework)</span></span>

<span data-ttu-id="30677-157">.NET Framework ' de `DataSet` `DataTable` bir denetim modu özelliği sağlayın.</span><span class="sxs-lookup"><span data-stu-id="30677-157">In .NET Framework, `DataSet` and `DataTable` provide an audit mode capability.</span></span> <span data-ttu-id="30677-158">Denetim modu etkin olduğunda `DataSet` ve `DataTable` gelen nesne türlerini izin verilen türler listesiyle karşılaştırırın.</span><span class="sxs-lookup"><span data-stu-id="30677-158">When audit mode is enabled, `DataSet` and `DataTable` compare the types of incoming objects against the allowed types list.</span></span> <span data-ttu-id="30677-159">Ancak, türüne izin verilmeyen bir nesne görüldüğünde, bir özel **durum oluşturulmaz.**</span><span class="sxs-lookup"><span data-stu-id="30677-159">However, if an object whose type is not allowed is seen, an exception is **not** thrown.</span></span> <span data-ttu-id="30677-160">Bunun yerine `DataSet` , `DataTable` `TraceListener` şüpheli bir türün mevcut olduğu tüm ekli örneklere bildirimde bulunur ve `TraceListener` Bu bilgileri günlüğe kaydetmek için izin verir.</span><span class="sxs-lookup"><span data-stu-id="30677-160">Instead, `DataSet` and `DataTable` notify any attached `TraceListener` instances that a suspicious type is present, allowing the `TraceListener` to log this information.</span></span> <span data-ttu-id="30677-161">Hiçbir özel durum oluşturulmaz ve seri durumundan çıkarma işlemi devam eder.</span><span class="sxs-lookup"><span data-stu-id="30677-161">No exception is thrown and the deserialization operation continues.</span></span>

> [!WARNING]
> <span data-ttu-id="30677-162">"Denetim modunda" bir uygulamanın çalıştırılması yalnızca test için kullanılan geçici bir ölçü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30677-162">Running an app in "audit mode" should only be a temporary measure used for testing.</span></span> <span data-ttu-id="30677-163">Denetim modu etkinleştirildiğinde `DataSet` ve `DataTable` uygulamanızın içinde bir güvenlik deliği ortaya çıkaracak tür kısıtlamalarını zorunlu kılmaz.</span><span class="sxs-lookup"><span data-stu-id="30677-163">When audit mode is enabled, `DataSet` and `DataTable` do not enforce type restrictions, which can introduce a security hole inside your app.</span></span> <span data-ttu-id="30677-164">Daha fazla bilgi için, [Güvenilmeyen girişle ilgili](#swr)olarak [tüm tür kısıtlamalarını](#ratr) ve güvenliği kaldırma başlıklı bölümlere bakın.</span><span class="sxs-lookup"><span data-stu-id="30677-164">For more information, see the sections titled [Removing all type restrictions](#ratr) and [Safety with regard to untrusted input](#swr).</span></span>

<span data-ttu-id="30677-165">Denetim modu, _App.config_aracılığıyla etkinleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="30677-165">Audit mode can be enabled through _App.config_:</span></span>

* <span data-ttu-id="30677-166">Öğe için konacak doğru değer hakkında bilgi için bu belgedeki [yapılandırma Ile genişletme](#etc) bölümüne bakın `<configSections>` .</span><span class="sxs-lookup"><span data-stu-id="30677-166">See the [Extending through configuration](#etc) section in this document for information on the proper value to put for the `<configSections>` element.</span></span>
* <span data-ttu-id="30677-167">`<allowedTypes auditOnly="true">`Aşağıdaki biçimlendirmede gösterildiği gibi denetleme modunu etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="30677-167">Use `<allowedTypes auditOnly="true">` to enable audit mode, as shown in the following markup.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="30677-168">Denetim modu etkinleştirildikten sonra, tercih ettiğiniz yerleşik _App.config_ `TraceListener` `DataSet` `TraceSource.` Izleme kaynağının adı _System. Data. DataSet_olan yerleşik bir bağlantı kurmak içinApp.configkullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30677-168">Once audit mode is enabled, you can use _App.config_ to connect your preferred `TraceListener` to the `DataSet` built-in `TraceSource.` The name of the built-in trace source is _System.Data.DataSet_.</span></span> <span data-ttu-id="30677-169">Aşağıdaki örnek, izleme olaylarını konsola _ve_ diskteki bir günlük dosyasına yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="30677-169">The following sample demonstrates writing trace events to the console _and_ to a log file on disk.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

<span data-ttu-id="30677-170">Ve hakkında daha fazla bilgi için `TraceSource` `TraceListener` bkz. [nasıl yapılır: Izleme dinleyicileri Ile TraceSource ve filtreler kullanma](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="30677-170">For more information on `TraceSource` and `TraceListener`, see the document [How to: Use TraceSource and Filters with Trace Listeners](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span>

> [!NOTE]
> <span data-ttu-id="30677-171">Bir uygulamayı denetim modunda çalıştırmak .NET Core veya .NET 5,0 ve üzeri sürümlerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="30677-171">Running an app in audit mode is not available in .NET Core or in .NET 5.0 and later.</span></span>

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a><span data-ttu-id="30677-172">Tüm tür kısıtlamalarını kaldır</span><span class="sxs-lookup"><span data-stu-id="30677-172">Remove all type restrictions</span></span>

<span data-ttu-id="30677-173">Bir uygulamanın tüm tür sınırlaması kısıtlamalarını ve ' den kaldırması `DataSet` gerekiyorsa `DataTable` :</span><span class="sxs-lookup"><span data-stu-id="30677-173">If an app must remove all type limiting restrictions from `DataSet` and `DataTable`:</span></span>

* <span data-ttu-id="30677-174">Tür sınırlandırma kısıtlamalarını bastırmak için çeşitli seçenekler vardır.</span><span class="sxs-lookup"><span data-stu-id="30677-174">There are several options to suppress type limiting restrictions.</span></span>
* <span data-ttu-id="30677-175">Kullanılabilir seçenekler, uygulamanın hedeflediği çerçeveye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="30677-175">The options available depend on the framework the app targets.</span></span>

> [!WARNING]
> <span data-ttu-id="30677-176">Tüm tür kısıtlamalarını kaldırmak, uygulamanın içinde bir güvenlik deliği ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-176">Removing all type restrictions can introduce a security hole inside the app.</span></span> <span data-ttu-id="30677-177">Bu mekanizmayı kullanırken, uygulamanın **not** `DataSet` `DataTable` Güvenilmeyen girişi okuyabilmesi ya da okumadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="30677-177">When using this mechanism, ensure the app does **not** use `DataSet` or `DataTable` to read untrusted input.</span></span> <span data-ttu-id="30677-178">Daha fazla bilgi için bkz. [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) ve [güvenilir olmayan girişle ilgili olarak güvenlik](#swr)başlıklı aşağıdaki bölüm.</span><span class="sxs-lookup"><span data-stu-id="30677-178">For more information, see [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) and the following section titled [Safety with regard to untrusted input](#swr).</span></span>

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a><span data-ttu-id="30677-179">AppContext yapılandırması aracılığıyla (.NET Framework 4,6-4,8, .NET Core 2,1 ve üzeri, .NET 5,0 ve üzeri)</span><span class="sxs-lookup"><span data-stu-id="30677-179">Through AppContext configuration (.NET Framework 4.6 - 4.8, .NET Core 2.1 and later, .NET 5.0 and later)</span></span>

<span data-ttu-id="30677-180">, `AppContext` , Olarak `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` ayarlandığında, ve ' `true` dan tüm tür sınırlandırma kısıtlamalarını kaldırır `DataSet` `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="30677-180">The `AppContext` switch, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation`, when set to `true` removes all type limiting restrictions from `DataSet` and `DataTable`.</span></span>

<span data-ttu-id="30677-181">.NET Framework, bu anahtar aşağıdaki yapılandırmada gösterildiği gibi _App.config_aracılığıyla etkinleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="30677-181">In .NET Framework, this switch can be enabled via _App.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

<span data-ttu-id="30677-182">ASP.NET içinde, `<AppContextSwitchOverrides>` öğesi kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="30677-182">In ASP.NET, the `<AppContextSwitchOverrides>` element is not available.</span></span> <span data-ttu-id="30677-183">Bunun yerine, aşağıdaki yapılandırmada gösterildiği gibi, anahtar _Web.config_aracılığıyla etkinleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="30677-183">Instead, the switch can be enabled via _Web.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="30677-184">Daha fazla bilgi için, bkz [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) . öğesi.</span><span class="sxs-lookup"><span data-stu-id="30677-184">For more information, see the [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element.</span></span>

<span data-ttu-id="30677-185">.NET Core, .NET 5 ve ASP.NET Core, bu ayar, aşağıdaki JSON 'da gösterildiği gibi, _runtimeconfig.js_tarafından denetlenir:</span><span class="sxs-lookup"><span data-stu-id="30677-185">In .NET Core, .NET 5, and ASP.NET Core, this setting is controlled by _runtimeconfig.json_, as shown in the following JSON:</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

<span data-ttu-id="30677-186">Daha fazla bilgi için bkz. [".NET Core çalışma zamanı yapılandırma ayarları"](/dotnet/core/run-time-config/).</span><span class="sxs-lookup"><span data-stu-id="30677-186">For more information, see [".NET Core run-time configuration settings"](/dotnet/core/run-time-config/).</span></span>

<span data-ttu-id="30677-187">`AllowArbitraryDataSetTypeInstantiation` , aşağıdaki kodda gösterildiği gibi, bir yapılandırma dosyası kullanmak yerine [AppContext. SetSwitch](/dotnet/api/system.appcontext.setswitch) aracılığıyla program aracılığıyla da ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="30677-187">`AllowArbitraryDataSetTypeInstantiation` can also be set programmatically via [AppContext.SetSwitch](/dotnet/api/system.appcontext.setswitch) instead of using a configuration file, as shown in the following code:</span></span>

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 <span data-ttu-id="30677-188">Önceki programlı yaklaşımı seçerseniz, çağrısı `AppContext.SetSwitch` uygulamalar başlangıcında erken gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="30677-188">If you choose the preceding programmatic approach, the call to `AppContext.SetSwitch` should occur early in the apps startup.</span></span>

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a><span data-ttu-id="30677-189">Makine genelindeki kayıt defteri aracılığıyla (.NET Framework 2,0-4,8)</span><span class="sxs-lookup"><span data-stu-id="30677-189">Through the machine-wide registry (.NET Framework 2.0 - 4.8)</span></span>

<span data-ttu-id="30677-190">`AppContext`Kullanılabilir değilse, tür sınırlandırma denetimleri Windows kayıt defteriyle devre dışı bırakılabilir:</span><span class="sxs-lookup"><span data-stu-id="30677-190">If `AppContext` is not available, type limiting checks can be disabled with the Windows registry:</span></span>

* <span data-ttu-id="30677-191">Bir yöneticinin kayıt defterini yapılandırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="30677-191">An administrator must configure the registry.</span></span>
* <span data-ttu-id="30677-192">Kayıt defterinin kullanılması makine genelinde bir değişiklik olduğundan makinede çalışan _Tüm_ uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="30677-192">Using the registry is a machine-wide change and will affect _all_ apps running on the machine.</span></span>

| <span data-ttu-id="30677-193">Tür</span><span class="sxs-lookup"><span data-stu-id="30677-193">Type</span></span>  |  <span data-ttu-id="30677-194">Değer</span><span class="sxs-lookup"><span data-stu-id="30677-194">Value</span></span> |
|---|---|
| <span data-ttu-id="30677-195">**Kayıt defteri anahtarı**</span><span class="sxs-lookup"><span data-stu-id="30677-195">**Registry key**</span></span> | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| <span data-ttu-id="30677-196">**Değer adı**</span><span class="sxs-lookup"><span data-stu-id="30677-196">**Value name**</span></span> | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| <span data-ttu-id="30677-197">**Değer türü**</span><span class="sxs-lookup"><span data-stu-id="30677-197">**Value type**</span></span> | `REG_SZ` |
| <span data-ttu-id="30677-198">**Değer verisi**</span><span class="sxs-lookup"><span data-stu-id="30677-198">**Value data**</span></span> | `true` |

<span data-ttu-id="30677-199">64 bitlik bir işletim sisteminde bu değerin hem 64 bit anahtar (yukarıda gösterilen) hem de 32-bit anahtarı için eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="30677-199">On a 64-bit operating system, this value my need to be added for both the 64-bit key (shown above) and the 32-bit key.</span></span> <span data-ttu-id="30677-200">32 bit anahtarı konumunda bulunur `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` .</span><span class="sxs-lookup"><span data-stu-id="30677-200">The 32-bit key is located at `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext`.</span></span>

<span data-ttu-id="30677-201">Yapılandırmak için kayıt defterini kullanma hakkında daha fazla bilgi için `AppContext` , bkz. ["kitaplık tüketicileri Için AppContext"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span><span class="sxs-lookup"><span data-stu-id="30677-201">For more information on using the registry to configure `AppContext`, see ["AppContext for library consumers"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span></span>

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a><span data-ttu-id="30677-202">Güvenilmeyen girişle ilgili güvenlik</span><span class="sxs-lookup"><span data-stu-id="30677-202">Safety with regard to untrusted input</span></span>

<span data-ttu-id="30677-203">Ancak `DataSet` `DataTable` , XML yüklerini seri durumdan çıkarma sırasında bulunmasına izin verilen türlerin varsayılan sınırlamalarını uygular __ `DataSet` ve `DataTable` Güvenilmeyen girişle doldurulurken genel olarak güvenli değildir.__</span><span class="sxs-lookup"><span data-stu-id="30677-203">While `DataSet` and `DataTable` do impose default limitations on the types that are allowed to be present while deserializing XML payloads, __`DataSet` and `DataTable` are in general not safe when populated with untrusted input.__</span></span> <span data-ttu-id="30677-204">Aşağıda, bir `DataSet` veya `DataTable` örneğinin güvenilmeyen girişi okuyabilme yöntemlerinin ayrıntılı olmayan bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="30677-204">The following is a non-exhaustive list of ways that a `DataSet` or `DataTable` instance might read untrusted input.</span></span>

* <span data-ttu-id="30677-205">Bir `DataAdapter` veritabanına başvurur ve `DataAdapter.Fill` yöntemi bir `DataSet` veritabanı sorgusunun içeriğiyle doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30677-205">A `DataAdapter` references a database, and the `DataAdapter.Fill` method is used to populate a `DataSet` with the contents of a database query.</span></span>
* <span data-ttu-id="30677-206">`DataSet.ReadXml`Or `DataTable.ReadXml` yöntemi, sütun ve satır bilgilerini IÇEREN bir XML dosyasını okumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30677-206">The `DataSet.ReadXml` or `DataTable.ReadXml` method is used to read an XML file containing column and row information.</span></span>
* <span data-ttu-id="30677-207">Bir `DataSet` veya `DataTable` örneği, bir ASP.net (SOAP) Web HIZMETLERININ veya WCF uç noktasının bir parçası olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="30677-207">A `DataSet` or `DataTable` instance is serialized as part of a ASP.NET (SOAP) web services or WCF endpoint.</span></span>
* <span data-ttu-id="30677-208">Bir seri hale getirici `XmlSerializer` , BIR `DataSet` XML akışından bir veya örneğinin serisini kaldırmak için kullanılır `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="30677-208">A serializer such as `XmlSerializer` is used to deserialize a `DataSet` or `DataTable` instance from an XML stream.</span></span>
* <span data-ttu-id="30677-209">Bir seri hale getirici `JsonConvert` , BIR `DataSet` JSON akışından bir veya örneğinin serisini kaldırmak için kullanılır `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="30677-209">A serializer such as `JsonConvert` is used to deserialize a `DataSet` or `DataTable` instance from a JSON stream.</span></span> <span data-ttu-id="30677-210">`JsonConvert` , kitaplığındaki popüler üçüncü taraf [Newtonsoft.Js](https://www.newtonsoft.com/json) bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="30677-210">`JsonConvert` is a method in the popular third-party [Newtonsoft.Json](https://www.newtonsoft.com/json) library.</span></span>
* <span data-ttu-id="30677-211">Bir seri hale getirici `BinaryFormatter` , `DataSet` ham bayt akışından bir veya örneğinin serisini kaldırmak için kullanılır `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="30677-211">A serializer such as `BinaryFormatter` is used to deserialize a `DataSet` or `DataTable` instance from a raw byte stream.</span></span>

<span data-ttu-id="30677-212">Bu belgede, yukarıdaki senaryolara yönelik güvenlik konuları ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30677-212">This document discusses safety considerations for the preceding scenarios.</span></span>

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a><span data-ttu-id="30677-213">`DataAdapter.Fill` `DataSet` Güvenilmeyen bir veri kaynağından doldurmak için kullanın</span><span class="sxs-lookup"><span data-stu-id="30677-213">Use `DataAdapter.Fill` to populate a `DataSet` from an untrusted data source</span></span>

<span data-ttu-id="30677-214">`DataSet` `DataAdapter` Aşağıdaki örnekte gösterildiği gibi, bir örnek, [ `DataAdapter.Fill` yöntemi](/dotnet/api/system.data.common.dataadapter.fill)kullanılarak bir öğesinden doldurulabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-214">A `DataSet` instance can be populated from a `DataAdapter` by using [the `DataAdapter.Fill` method](/dotnet/api/system.data.common.dataadapter.fill), as shown in the following example.</span></span>

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

<span data-ttu-id="30677-215">(Yukarıdaki kod örneği, [DataAdapter nesnesinden bir veri kümesini doldururken](../populating-a-dataset-from-a-dataadapter.md)bulunan daha büyük bir örneğin bir parçasıdır.)</span><span class="sxs-lookup"><span data-stu-id="30677-215">(The code sample above is part of a larger sample found at [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)</span></span>

> <span data-ttu-id="30677-216">Çoğu uygulama basitleşebilir ve veritabanı katmanının güvenilir olduğunu varsayabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-216">Most apps can simplify and assume that their database layer is trusted.</span></span> <span data-ttu-id="30677-217">Bununla birlikte, uygulamalarınızın iş [modellemesinin](https://www.microsoft.com/securityengineering/sdl/threatmodeling) bir habiti varsa, tehdit modeliniz uygulama (istemci) ile veritabanı katmanı (sunucu) arasında bir güven sınırı olduğunu göz önünde bulundurmayabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-217">However, if you are in the habit of [threat modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) your apps, your threat model may consider there to be a trust boundary between the application (client) and database layer (server).</span></span> <span data-ttu-id="30677-218">İstemci ve sunucu arasında [karşılıklı kimlik doğrulama](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) veya [AAD kimlik doğrulaması](/azure/azure-sql/database/authentication-aad-overview) kullanmak, bununla ilişkili riskleri karşılamak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="30677-218">Using [mutual authentication](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) or [AAD authentication](/azure/azure-sql/database/authentication-aad-overview) between client and server is one way to help address the risks associated with this.</span></span> <span data-ttu-id="30677-219">Bu bölümün geri kalanında güvenilmeyen sunucuya bağlanan istemcinin olası sonucu ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30677-219">The remainder of this section discusses the possible result of a client connecting to an untrusted server.</span></span>

<span data-ttu-id="30677-220">`DataAdapter`Güvenilir olmayan bir veri kaynağına işaret eden sonuçlar kendisinin uygulamasına bağlıdır `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="30677-220">The consequences of pointing a `DataAdapter` at an untrusted data source depend on the implementation of the `DataAdapter` itself.</span></span>

### <a name="sqldataadapter"></a><span data-ttu-id="30677-221">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="30677-221">SqlDataAdapter</span></span>

<span data-ttu-id="30677-222">Yerleşik tür [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter)için, güvenilmeyen bir veri kaynağına başvurmak, hizmet reddi (DOS) saldırısının oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-222">For the built-in type [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), referencing an untrusted data source could result in a denial of service (DoS) attack.</span></span> <span data-ttu-id="30677-223">DoS saldırısı, uygulamanın yanıt vermemesine veya kilitlenmelerine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-223">The DoS attack could result in the app becoming unresponsive or crashing.</span></span> <span data-ttu-id="30677-224">Bir saldırgan uygulama ile birlikte bir DLL 'yi kurtabiliyor ise, yerel kod yürütmeye de ulaşabiliyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-224">If an attacker can plant a DLL alongside the app, they may also be able to achieve local code execution.</span></span>

### <a name="other-dataadapter-types"></a><span data-ttu-id="30677-225">Diğer DataAdapter türleri</span><span class="sxs-lookup"><span data-stu-id="30677-225">Other DataAdapter types</span></span>

<span data-ttu-id="30677-226">Üçüncü taraf `DataAdapter` uygulamaları, güvenilmeyen girişler karşısında sağladıkları güvenlik garantisi hakkında kendi değerlendirmelerini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="30677-226">Third-party `DataAdapter` implementations must make their own assessments about what security guarantees they provide in the face of untrusted inputs.</span></span> <span data-ttu-id="30677-227">.NET, bu uygulamalarla ilgili herhangi bir güvenlik garantisi yapamaz.</span><span class="sxs-lookup"><span data-stu-id="30677-227">.NET cannot make any safety guarantees regarding these implementations.</span></span>

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a><span data-ttu-id="30677-228">DataSet. ReadXml ve DataTable. ReadXml</span><span class="sxs-lookup"><span data-stu-id="30677-228">DataSet.ReadXml and DataTable.ReadXml</span></span>

<span data-ttu-id="30677-229">`DataSet.ReadXml`Ve `DataTable.ReadXml` yöntemleri güvenilmeyen girişle kullanıldığında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="30677-229">The `DataSet.ReadXml` and `DataTable.ReadXml` methods are not safe when used with untrusted input.</span></span> <span data-ttu-id="30677-230">Bunun yerine, bu belgede daha sonra özetlenen alternatifden birini kullanmayı düşünmemiz önerilir.</span><span class="sxs-lookup"><span data-stu-id="30677-230">We strongly recommend that consumers instead consider using one of the alternatives outlined later in this document.</span></span>

<span data-ttu-id="30677-231">`DataSet.ReadXml`Ve uygulamaları `DataTable.ReadXml` serileştirme güvenlik açıklarına göre ilk başta oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="30677-231">The implementations of `DataSet.ReadXml` and `DataTable.ReadXml` were originally created before serialization vulnerabilities were a well-understood threat category.</span></span> <span data-ttu-id="30677-232">Sonuç olarak, kod geçerli en iyi güvenlik uygulamalarını izlemez.</span><span class="sxs-lookup"><span data-stu-id="30677-232">As a result, the code does not follow current security best practices.</span></span> <span data-ttu-id="30677-233">Bu API 'Ler, saldırganların Web uygulamalarına yönelik DoS saldırıları gerçekleştirmesine yönelik vektörler olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-233">These APIs can be used as vectors for attackers to perform DoS attacks against web apps.</span></span> <span data-ttu-id="30677-234">Bu saldırılar, Web hizmetini yanıt vermemeye veya beklenmeyen işlem sonlandırmasına neden olarak işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="30677-234">These attacks might render the web service unresponsive or result in unexpected process termination.</span></span> <span data-ttu-id="30677-235">Framework bu saldırı kategorilerine yönelik azaltmaları sağlamaz ve .NET bu davranışı "tasarıma göre" kabul eder.</span><span class="sxs-lookup"><span data-stu-id="30677-235">The framework does not provide mitigations for these attack categories and .NET considers this behavior "by design".</span></span>

<span data-ttu-id="30677-236">.NET, ve ' de bilgi açığa çıkması veya uzaktan kod yürütme gibi bazı sorunları azaltmak için güvenlik güncelleştirmeleri yayımlamıştır `DataSet.ReadXml` `DataTable.ReadXml` .</span><span class="sxs-lookup"><span data-stu-id="30677-236">.NET has released security updates to mitigate some issues such as information disclosure or remote code execution in `DataSet.ReadXml` and `DataTable.ReadXml`.</span></span> <span data-ttu-id="30677-237">.NET güvenlik güncelleştirmeleri, bu tehdit kategorilerine karşı tamamen koruma sağlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-237">The .NET security updates may not provide complete protection against these threat categories.</span></span> <span data-ttu-id="30677-238">Tüketiciler, bağımsız senaryolarını değerlendirmeli ve bu risklerle ilgili olası pozlandırmayı göz önünde bulundurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30677-238">Consumers should assess their individual scenarios and consider their potential exposure to these risks.</span></span>

<span data-ttu-id="30677-239">Tüketiciler, bu API 'lere yönelik güvenlik güncelleştirmelerinin bazı durumlarda uygulama uyumluluğunu etkileyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="30677-239">Consumers should be aware that security updates to these APIs may impact application compatibility in some situations.</span></span> <span data-ttu-id="30677-240">Ayrıca, bu API 'lerde bir nobir güvenlik açığı bulduğundan, .NET 'in bir güvenlik güncelleştirmesini yayımlayabileceği bir olasılık vardır.</span><span class="sxs-lookup"><span data-stu-id="30677-240">Furthermore, the possibility exists that a novel vulnerability in these APIs will be discovered for which .NET can't practically publish a security update.</span></span>

<span data-ttu-id="30677-241">Bu API 'lerin tüketicilerinin şunları yapmanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="30677-241">We recommend that consumers of these APIs either:</span></span>

* <span data-ttu-id="30677-242">Bu belgede daha sonra özetlenen alternatifden birini kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="30677-242">Consider using one of the alternatives outlined later in this document.</span></span>
* <span data-ttu-id="30677-243">Uygulamalarda bireysel risk değerlendirmeleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="30677-243">Perform individual risk assessments on their apps.</span></span>

<span data-ttu-id="30677-244">Bu API 'Lerin kullanılıp kullanılmayacağını belirleme tüketicinin tek sorumluluğudur.</span><span class="sxs-lookup"><span data-stu-id="30677-244">It is the consumer's sole responsibility to determine whether to utilize these APIs.</span></span> <span data-ttu-id="30677-245">Tüketiciler, bu API 'Leri kullanarak eşlik eden, yasal gereksinimleri de içeren tüm güvenlik, teknik ve yasal riskleri değerlendirmelidir.</span><span class="sxs-lookup"><span data-stu-id="30677-245">Consumers should assess any security, technical, and legal risks, including regulatory requirements, that may accompany using these APIs.</span></span>

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a><span data-ttu-id="30677-246">ASP.NET Web Hizmetleri veya WCF aracılığıyla veri kümesi ve DataTable</span><span class="sxs-lookup"><span data-stu-id="30677-246">DataSet and DataTable via ASP.NET web services or WCF</span></span>

<span data-ttu-id="30677-247">`DataSet` `DataTable` Aşağıdaki kodda gösterildiği gibi, bir ASP.net (SOAP) Web hizmetinde bir veya örneği kabul etmek mümkündür:</span><span class="sxs-lookup"><span data-stu-id="30677-247">It is possible to accept a `DataSet` or a `DataTable` instance in an ASP.NET (SOAP) web service, as demonstrated in the following code:</span></span>

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

<span data-ttu-id="30677-248">Bu bir varyasyon, `DataSet` `DataTable` bir parametre olarak kabul edilmez veya doğrudan, aşağıdaki kodda gösterildiği gıbı Genel SOAP serileştirilmiş nesne grafiğinin bir parçası olarak kabul edilmez:</span><span class="sxs-lookup"><span data-stu-id="30677-248">A variation on this is not to accept `DataSet` or `DataTable` directly as a parameter, but instead to accept it as part of the overall SOAP serialized object graph, as shown in the following code:</span></span>

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="30677-249">Ya da ASP.NET Web Hizmetleri yerine WCF kullanma:</span><span class="sxs-lookup"><span data-stu-id="30677-249">Or, using WCF instead of ASP.NET web services:</span></span>

```cs
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="30677-250">Bu durumların tümünde, tehdit modeli ve güvenlik garantisi, [DataSet. ReadXml ve DataTable. ReadXml bölümü](#dsrdtr)ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="30677-250">In all of these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr).</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a><span data-ttu-id="30677-251">XmlSerializer aracılığıyla bir veri kümesi veya DataTable serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="30677-251">Deserialize a DataSet or DataTable via XmlSerializer</span></span>

<span data-ttu-id="30677-252">Geliştiriciler `XmlSerializer` `DataSet` `DataTable` , aşağıdaki kodda gösterildiği gibi, serisini kaldırmak ve örnekleri için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="30677-252">Developers can use `XmlSerializer` to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```cs
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="30677-253">Bu durumlarda, tehdit modeli ve güvenlik garantisi, [DataSet. ReadXml ve DataTable. ReadXml bölümüyle](#dsrdtr) aynıdır</span><span class="sxs-lookup"><span data-stu-id="30677-253">In these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr)</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a><span data-ttu-id="30677-254">JsonConvert aracılığıyla bir veri kümesi veya DataTable serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="30677-254">Deserialize a DataSet or DataTable via JsonConvert</span></span>

<span data-ttu-id="30677-255">Popüler üçüncü taraf Newtonsoft Library [JSON.net](https://www.newtonsoft.com/json) `DataSet` `DataTable` , aşağıdaki kodda gösterildiği gibi seri durumdan çıkarılacak ve örnekleri için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="30677-255">The popular third-party Newtonsoft library [JSON.NET](https://www.newtonsoft.com/json) can be used to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```cs
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObect<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObect<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="30677-256">Güvenilmeyen bir `DataSet` `DataTable` JSON blobundan bu şekilde veya bu şekilde seri durumdan çıkarmak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="30677-256">Deserializing a `DataSet` or `DataTable` in this manner from an untrusted JSON blob is not safe.</span></span> <span data-ttu-id="30677-257">Bu model, hizmet reddi saldırılarına karşı savunmasızdır.</span><span class="sxs-lookup"><span data-stu-id="30677-257">This pattern is vulnerable to a denial of service attack.</span></span> <span data-ttu-id="30677-258">Bu tür bir saldırı, uygulamayı kilitlerler veya yanıt vermemeye işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="30677-258">Such an attack could crash the app or render it unresponsive.</span></span>

> [!NOTE]
> <span data-ttu-id="30677-259">Microsoft, _Newtonsoft.Js_gibi üçüncü taraf kitaplıkların uygulanmasını garanti etmez veya desteklemez.</span><span class="sxs-lookup"><span data-stu-id="30677-259">Microsoft does not warrant or support the implementation of third-party libraries like _Newtonsoft.Json_.</span></span> <span data-ttu-id="30677-260">Bu bilgiler, tamamlanma zamanı için sağlanır ve bu yazma zamanından itibaren doğru olur.</span><span class="sxs-lookup"><span data-stu-id="30677-260">This information is provided for completeness and is accurate as of the time of this writing.</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a><span data-ttu-id="30677-261">BinaryFormatter aracılığıyla DataSet veya DataTable serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="30677-261">Deserialize a DataSet or DataTable via BinaryFormatter</span></span>

<span data-ttu-id="30677-262">Geliştiricilerin `BinaryFormatter` `NetDataContractSerializer` `SoapFormatter` Güvenilmeyen bir yükün veya örneğinin serisini kaldırmak için hiçbir şekilde,, veya ilgili ***güvenli olmayan*** biçimleri kullanması gerekir `DataSet` `DataTable` :</span><span class="sxs-lookup"><span data-stu-id="30677-262">Developers must never use `BinaryFormatter`, `NetDataContractSerializer`, `SoapFormatter`, or related ***unsafe*** formatters to deserialize a `DataSet` or `DataTable` instance from an untrusted payload:</span></span>

* <span data-ttu-id="30677-263">Bu, tam bir uzaktan kod yürütme saldırısından etkilenir.</span><span class="sxs-lookup"><span data-stu-id="30677-263">This is susceptible to a full remote code execution attack.</span></span>
* <span data-ttu-id="30677-264">`SerializationBinder`Bu tür bir saldırıyı engellemek için özel kullanımı yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="30677-264">Using a custom `SerializationBinder` is not sufficient to prevent such an attack.</span></span>

## <a name="safe-replacements"></a><span data-ttu-id="30677-265">Güvenli değişiklikler</span><span class="sxs-lookup"><span data-stu-id="30677-265">Safe replacements</span></span>

<span data-ttu-id="30677-266">Şu iki uygulama için:</span><span class="sxs-lookup"><span data-stu-id="30677-266">For apps that either:</span></span>

* <span data-ttu-id="30677-267">`DataSet` `DataTable` . Asmx SOAP uç noktasını veya WCF uç noktasını kabul edin.</span><span class="sxs-lookup"><span data-stu-id="30677-267">Accept `DataSet` or `DataTable` through an .asmx SOAP endpoint or a WCF endpoint.</span></span>
* <span data-ttu-id="30677-268">Güvenilmeyen verileri veya örneğine serisini kaldırma `DataSet` `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="30677-268">Deserialize untrusted data into an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="30677-269">Nesne modelini [Entity Framework](/ef)kullanacak şekilde değiştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="30677-269">Consider replacing the object model to use [Entity Framework](/ef).</span></span> <span data-ttu-id="30677-270">Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="30677-270">Entity Framework:</span></span>

* <span data-ttu-id="30677-271">, İlişkisel verileri temsil eden zengin, modern, nesne odaklı bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="30677-271">Is a rich, modern, object-oriented framework that can represent relational data.</span></span>
* <span data-ttu-id="30677-272">Veritabanı sorgularının Entity Framework nesne modelleriniz aracılığıyla proje veritabanını kolayca sunmayı kolaylaştırmak için, veritabanı sağlayıcılarının [farklı bir ekosistemini](/ef/core/providers/) getirir.</span><span class="sxs-lookup"><span data-stu-id="30677-272">Brings [a diverse ecosystem](/ef/core/providers/) of database providers to make it easy to project database queries via your Entity Framework object models.</span></span>
* <span data-ttu-id="30677-273">Güvenilmeyen kaynaklardan veri serisini kaldırırken yerleşik korumalar sunar.</span><span class="sxs-lookup"><span data-stu-id="30677-273">Offers built-in protections when deserializing data from untrusted sources.</span></span>

<span data-ttu-id="30677-274">`.aspx`SOAP uç noktaları kullanan uygulamalar için, bu uç noktaları [WCF](/dotnet/framework/wcf/)kullanacak şekilde değiştirmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="30677-274">For apps that use `.aspx` SOAP endpoints, consider changing those endpoints to use [WCF](/dotnet/framework/wcf/).</span></span> <span data-ttu-id="30677-275">WCF, Web Hizmetleri için daha tam özellikli bir değiştirme işlemi `.asmx` .</span><span class="sxs-lookup"><span data-stu-id="30677-275">WCF is a more fully featured replacement for `.asmx` web services.</span></span> <span data-ttu-id="30677-276">WCF uç noktaları, mevcut çağıranlar ile uyumluluk için [SOAP aracılığıyla gösterilebilir](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) .</span><span class="sxs-lookup"><span data-stu-id="30677-276">WCF endpoints [can be exposed via SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) for compatibility with existing callers.</span></span>

## <a name="code-analyzers"></a><span data-ttu-id="30677-277">Kod çözümleyicileri</span><span class="sxs-lookup"><span data-stu-id="30677-277">Code analyzers</span></span>

<span data-ttu-id="30677-278">Kaynak kodunuz derlendiğinde çalıştırılan kod Çözümleyicisi güvenlik kuralları, C# ve Visual Basic kodundaki bu güvenlik sorunuyla ilgili güvenlik açıklarını bulmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="30677-278">Code analyzer security rules, which run when your source code is compiled, can help to find vulnerabilities related to this security issue in C# and Visual Basic code.</span></span> <span data-ttu-id="30677-279">Microsoft. CodeAnalysis. Fxcopçözümleyiciler, [NuGet.org](https://www.nuget.org/)üzerinde dağıtılan kod Çözümleyicileri 'Nin bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="30677-279">Microsoft.CodeAnalysis.FxCopAnalyzers is a NuGet package of code analyzers that's distributed on [nuget.org](https://www.nuget.org/).</span></span>

<span data-ttu-id="30677-280">Kod çözümleyicilerine genel bakış için bkz. [kaynak kodu Çözümleyicileri 'Ne genel bakış](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).</span><span class="sxs-lookup"><span data-stu-id="30677-280">For an overview of code analyzers, see [Overview of source code analyzers](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

<span data-ttu-id="30677-281">Aşağıdaki Microsoft. CodeAnalysis. Fxcopçözümleyiciler kurallarını etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="30677-281">Enable the following Microsoft.CodeAnalysis.FxCopAnalyzers rules:</span></span>

- <span data-ttu-id="30677-282">[CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): güvenilmeyen verilerle DataTable. ReadXml () kullanmayın</span><span class="sxs-lookup"><span data-stu-id="30677-282">[CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): Do not use DataTable.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="30677-283">[CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): veri kümesi. ReadXml () öğesini güvenilmeyen verilerle kullanma</span><span class="sxs-lookup"><span data-stu-id="30677-283">[CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): Do not use DataSet.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="30677-284">[CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): serileştirilebilir türdeki güvenli olmayan veri kümesi veya DataTable, uzak kod yürütme saldırılarına karşı savunmasız olabilir</span><span class="sxs-lookup"><span data-stu-id="30677-284">[CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): Unsafe DataSet or DataTable in serializable type can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="30677-285">[CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): Serializable türde güvenli olmayan veri kümesi veya DataTable</span><span class="sxs-lookup"><span data-stu-id="30677-285">[CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): Unsafe DataSet or DataTable in serializable type</span></span>
- <span data-ttu-id="30677-286">[CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): Serisi kaldırılan nesne grafiğinde güvenli olmayan veri kümesi veya DataTable, uzak kod yürütme saldırılarına karşı savunmasız olabilir</span><span class="sxs-lookup"><span data-stu-id="30677-286">[CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): Unsafe DataSet or DataTable in deserialized object graph can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="30677-287">[CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): serisi kaldırılabilir nesne grafiğinde güvenli olmayan veri kümesi veya DataTable türü bulundu</span><span class="sxs-lookup"><span data-stu-id="30677-287">[CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): Unsafe DataSet or DataTable type found in deserializable object graph</span></span>
- <span data-ttu-id="30677-288">[CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): Web 'in seri hale getirilebilir nesne grafiğinde güvenli olmayan veri kümesi veya DataTable türü</span><span class="sxs-lookup"><span data-stu-id="30677-288">[CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): Unsafe DataSet or DataTable type in web deserializable object graph</span></span>
- <span data-ttu-id="30677-289">[CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): DataSet. ReadXml () içeren bir otomatik olarak oluşturulan sınıfın güvenilmeyen verilerle kullanılmadığından emin olun</span><span class="sxs-lookup"><span data-stu-id="30677-289">[CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): Ensure autogenerated class containing DataSet.ReadXml() is not used with untrusted data</span></span>
- <span data-ttu-id="30677-290">[CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): otomatik olarak seri hale getirilebilir türde veri kümesi veya DataTable, uzaktan kod yürütme saldırılarına karşı savunmasız olabilir</span><span class="sxs-lookup"><span data-stu-id="30677-290">[CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): Unsafe DataSet or DataTable in autogenerated serializable type can be vulnerable to remote code execution attacks</span></span>

<span data-ttu-id="30677-291">Kuralları yapılandırma hakkında daha fazla bilgi için bkz. [kod Çözümleyicileri kullanma](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).</span><span class="sxs-lookup"><span data-stu-id="30677-291">For more information about configuring rules, see [Use code analyzers](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).</span></span>

<span data-ttu-id="30677-292">Yeni güvenlik kuralları aşağıdaki NuGet paketlerinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="30677-292">The new security rules are available in the following NuGet packages:</span></span>

- <span data-ttu-id="30677-293">Microsoft. CodeAnalysis. Fxcopçözümleyiciler 3.3.0: Visual Studio 2019 sürüm 16,3 veya üzeri için</span><span class="sxs-lookup"><span data-stu-id="30677-293">Microsoft.CodeAnalysis.FxCopAnalyzers 3.3.0: for Visual Studio 2019 version 16.3 or later</span></span>
- <span data-ttu-id="30677-294">Microsoft. CodeAnalysis. Fxcopçözümleyiciler 2.9.11: Visual Studio 2017 sürüm 15,9 veya üzeri için</span><span class="sxs-lookup"><span data-stu-id="30677-294">Microsoft.CodeAnalysis.FxCopAnalyzers 2.9.11: for Visual Studio 2017 version 15.9 or later</span></span>
