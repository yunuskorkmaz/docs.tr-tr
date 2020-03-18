---
title: İkili serileştirme
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: 9df9b73a1a1347b952d76b76c9058578f5e9f401
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400640"
---
# <a name="binary-serialization"></a><span data-ttu-id="ea29f-102">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="ea29f-102">Binary serialization</span></span>

<span data-ttu-id="ea29f-103">Serileştirme depolama ortamına bir nesne durumunu depolama işlemi olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ea29f-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="ea29f-104">Bu işlem sırasında, nesnenin ortak ve özel alanları ve sınıfı içeren derleme de dahil olmak üzere sınıfın adı, daha sonra bir veri akışına yazılır bayt akışına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="ea29f-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="ea29f-105">Nesnenin seri durumdan daha sonra orijinal nesneyi tam bir kopyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ea29f-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="ea29f-106">Nesne yönelimli bir ortamda bir serileştirme mekanizması uygularken, kullanım kolaylığı ve esneklik arasında bir dizi dengeleme yapmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="ea29f-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="ea29f-107">İşlem üzerinde yeterli denetim iniz verilmesi koşuluyla, işlem büyük ölçüde otomatikleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ea29f-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="ea29f-108">Örneğin, burada basit ikili serileştirme yeterli değil veya bir sınıf hangi alanları seri hale gerek karar vermek için belirli bir neden olabilir durumlarda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="ea29f-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="ea29f-109">Aşağıdaki bölümlerde .NET ile sağlanan sağlam serileştirme mekanizmasını inceler ve gereksinimlerinizi karşılamak için işlemi özelleştirmenize olanak tanıyan bir dizi önemli özelliği vurgular.</span><span class="sxs-lookup"><span data-stu-id="ea29f-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="ea29f-110">Nesnenin serileştirildiği ve farklı .NET Framework sürümleri kullanılarak seri durumdan UTF-8 veya UTF-7 kodlanmış nesne durumunu korunur değil.</span><span class="sxs-lookup"><span data-stu-id="ea29f-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="ea29f-111">İkili serileştirme, bir nesnenin içindeki özel üyeleri değiştirmenize ve bu nedenle nesnenin durumunu değiştirmeye olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ea29f-111">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="ea29f-112">Bu nedenle, genel API yüzeyinde <xref:System.Text.Json?displayProperty=fullName>çalışan diğer serileştirme çerçeveleri önerilir.</span><span class="sxs-lookup"><span data-stu-id="ea29f-112">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="ea29f-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea29f-113">.NET Core</span></span>

<span data-ttu-id="ea29f-114">.NET Core, bir tür alt kümesi için ikili serileştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="ea29f-114">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="ea29f-115">Aşağıdaki [Serializable türleri](#serializable-types) bölümünde desteklenen türlerin listesini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea29f-115">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="ea29f-116">Listelenen türlerin .NET Framework 4.5.1 ve sonraki sürümler arasında ve .NET Core 2.0 ve sonraki sürümler arasında serileştirilebilir olması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="ea29f-116">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="ea29f-117">Mono gibi diğer .NET uygulamaları resmi olarak desteklenmez, ancak aynı zamanda çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea29f-117">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="ea29f-118">Serializable türleri</span><span class="sxs-lookup"><span data-stu-id="ea29f-118">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="ea29f-119">Tür</span><span class="sxs-lookup"><span data-stu-id="ea29f-119">Type</span></span> | <span data-ttu-id="ea29f-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="ea29f-120">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-121">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-121">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-122">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-122">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-123">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-124">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-125">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-126">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-127">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-128">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-129">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-130">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-131">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-132">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-133">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-134">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-134">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="ea29f-135">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-136">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-136">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-137">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-138">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-139">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-140">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-140">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="ea29f-141">.NET Framework'den .NET Core'a serileştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ea29f-141">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-142">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-142">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="ea29f-143">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-143">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-144">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-145">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-146">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-147">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-148">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-149">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-150">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="ea29f-151">.NET Core 2.0.2 ve sonraki sürümlerde başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-151">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-152">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-153">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-153">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-154">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-155">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="ea29f-156">`SerializationFormat.Binary`Ayarlarsanız, `RemotingFormat` yalnızca .NET Core 2.1 ve sonraki sürümlerle değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ea29f-156">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-157">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-158">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-158">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-159">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-160">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-161">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-162">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-163">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-164">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-165">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-166">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-167">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-168">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-169">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-169">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="ea29f-170">.NET Framework'den .NET Core'a serileştirme desteklenmez</span><span class="sxs-lookup"><span data-stu-id="ea29f-170">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-171">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-171">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-172">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-172">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-173">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-174">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-175">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-176">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-177">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-178">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-179">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="ea29f-180">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-181">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-182">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-183">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-184">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-185">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-186">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-187">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-188">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-189">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-190">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-191">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-192">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-193">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-194">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-195">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-196">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-197">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-198">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-199">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-200">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-201">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-202">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-203">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-204">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-205">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="ea29f-206">.NET Core 2.0.6'dan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-206">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-207">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-208">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-208">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-209">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-210">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="ea29f-211">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-212">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-213">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-214">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-215">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-216">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-217">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-218">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-219">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-220">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-221">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-222">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-223">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-224">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-225">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-226">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-227">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-228">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-229">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-230">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-231">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-232">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-233">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-234">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-235">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-236">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-237">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-238">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-239">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-240">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-241">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-242">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-243">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-244">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-245">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-246">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-247">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-248">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-249">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-250">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-251">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-252">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-253">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-254">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-255">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-256">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-257">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-258">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-259">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-259">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="ea29f-260">.NET Framework'den .NET Core'a serileştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ea29f-260">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-261">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-261">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-262">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-262">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-263">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-264">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-265">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-266">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-267">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-268">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-269">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-270">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-271">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-272">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-273">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-274">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-275">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-276">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-277">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-278">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-279">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-280">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-281">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-281">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="ea29f-282">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-283">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-283">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-284">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-285">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-286">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-286">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="ea29f-287">Sınırlı serileştirme verileri.</span><span class="sxs-lookup"><span data-stu-id="ea29f-287">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-288">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-288">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-289">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-289">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-290">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-291">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-292">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-293">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-294">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-295">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-296">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-297">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-298">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-299">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-300">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-301">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-302">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-303">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-304">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-305">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-306">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-307">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-308">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-309">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-310">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-311">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-312">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-313">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-314">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-315">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-316">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-317">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-318">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-319">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-320">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="ea29f-321">.NET Framework 4.7 ve önceki sürümlerde serileştirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="ea29f-321">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-322">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-323">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-323">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-324">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-325">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-326">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-327">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="ea29f-328">.NET Core 2.0.4'ten başlayarak.</span><span class="sxs-lookup"><span data-stu-id="ea29f-328">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ea29f-329">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea29f-329">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="ea29f-330">Serileştirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="ea29f-330">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="ea29f-331">[XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="ea29f-331">[XML and SOAP Serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="ea29f-332">Ortak dil çalışma zamanı ile içerdiği XML serileştirme mekanizması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea29f-332">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="ea29f-333">[Güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="ea29f-333">[Security and Serialization](../../../docs/framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="ea29f-334">Serileştirme gerçekleştiren kod yazarken izlemek için güvenli kodlama yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ea29f-334">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="ea29f-335">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ea29f-335">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="ea29f-336">Uzaktan iletişim için .NET Framework'de başlayan çeşitli yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ea29f-336">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="ea29f-337">[ASP.NET ve XML Web Hizmeti İstemcileri Kullanılarak Oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ea29f-337">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="ea29f-338">ASP.NET kullanılarak oluşturulan XML Web hizmetlerinin nasıl programlandığını açıklayan ve açıklayan makaleler.</span><span class="sxs-lookup"><span data-stu-id="ea29f-338">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
