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
# <a name="binary-serialization"></a><span data-ttu-id="65065-102">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="65065-102">Binary serialization</span></span>

<span data-ttu-id="65065-103">Serileştirme depolama ortamına bir nesne durumunu depolama işlemi olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="65065-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="65065-104">Bu işlem sırasında, nesnenin ortak ve özel alanları ile sınıfın adı, sınıfı içeren derleme dahil olmak üzere, bir veri akışına yazılan bayt akışına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="65065-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="65065-105">Nesnenin seri durumdan daha sonra orijinal nesneyi tam bir kopyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="65065-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="65065-106">Bir serileştirme mekanizmasını nesne yönelimli bir ortamda uygularken, kullanım kolaylığı ve esneklik arasında bir dizi denge yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="65065-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="65065-107">Süreç üzerinde yeterli denetim verildiğinden işlem, büyük bir ölçüde otomatik olabilir.</span><span class="sxs-lookup"><span data-stu-id="65065-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="65065-108">Örneğin, burada basit ikili serileştirme yeterli değil veya bir sınıf hangi alanları seri hale gerek karar vermek için belirli bir neden olabilir durumlarda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="65065-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="65065-109">Aşağıdaki bölümlerde .NET ile sunulan güçlü serileştirme mekanizması incelenecektir ve bu işlemi gereksinimlerinizi karşılayacak şekilde özelleştirmenize imkan tanıyan bazı önemli özellikler vurgulanacak.</span><span class="sxs-lookup"><span data-stu-id="65065-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="65065-110">Nesnenin serileştirildiği ve farklı .NET Framework sürümleri kullanılarak seri durumdan UTF-8 veya UTF-7 kodlanmış nesne durumunu korunur değil.</span><span class="sxs-lookup"><span data-stu-id="65065-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="65065-111">İkili serileştirme bir nesne içindeki özel üyelerin değiştirilmesini ve bu nedenle durumunun değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="65065-111">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="65065-112">Bu nedenle, ortak API yüzeyinde çalışan gibi <xref:System.Text.Json?displayProperty=fullName>diğer serileştirme çerçeveleri önerilir.</span><span class="sxs-lookup"><span data-stu-id="65065-112">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="65065-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="65065-113">.NET Core</span></span>

<span data-ttu-id="65065-114">.NET Core bir tür alt kümesi için ikili serileştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="65065-114">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="65065-115">Desteklenen türlerin listesini aşağıdaki [seri hale getirilebilir türler](#serializable-types) bölümünde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65065-115">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="65065-116">Listelenen türlerin .NET Framework 4.5.1 ve sonraki sürümleri ile .NET Core 2,0 ve sonraki sürümleri arasında seri hale getirilebilir olduğu garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="65065-116">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="65065-117">Mono gibi diğer .NET uygulamaları resmi olarak desteklenmez, ancak aynı zamanda çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="65065-117">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="65065-118">Serileştirilebilir türler</span><span class="sxs-lookup"><span data-stu-id="65065-118">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="65065-119">Tür</span><span class="sxs-lookup"><span data-stu-id="65065-119">Type</span></span> | <span data-ttu-id="65065-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="65065-120">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="65065-121">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-121">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="65065-122">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-122">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="65065-123">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="65065-124">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="65065-125">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="65065-126">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="65065-127">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="65065-128">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="65065-129">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="65065-130">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="65065-131">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="65065-132">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="65065-133">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-134">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-134">Starting in .NET Core 2.0.4.</span></span> |
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
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="65065-135">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="65065-136">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-136">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="65065-137">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="65065-138">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="65065-139">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="65065-140">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-140">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="65065-141">.NET Framework 'den .NET Core 'a serileştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="65065-141">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="65065-142">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-142">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="65065-143">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-143">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="65065-144">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="65065-145">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="65065-146">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="65065-147">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-148">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="65065-149">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="65065-150">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="65065-151">.NET Core 2.0.2 ve sonraki sürümlerde başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="65065-151">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="65065-152">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="65065-153">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-153">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="65065-154">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="65065-155">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="65065-156">`SerializationFormat.Binary`' A ayarlarsanız `RemotingFormat` , yalnızca .NET Core 2,1 ve sonraki sürümlerle değiş tokuş edilebilir.</span><span class="sxs-lookup"><span data-stu-id="65065-156">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="65065-157">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="65065-158">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-158">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="65065-159">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="65065-160">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="65065-161">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="65065-162">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="65065-163">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="65065-164">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="65065-165">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="65065-166">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="65065-167">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="65065-168">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="65065-169">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-169">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="65065-170">.NET Framework 'den .NET Core 'a serileştirme desteklenmez</span><span class="sxs-lookup"><span data-stu-id="65065-170">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="65065-171">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-171">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="65065-172">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-172">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="65065-173">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="65065-174">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="65065-175">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="65065-176">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="65065-177">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-178">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="65065-179">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="65065-180">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="65065-181">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-182">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="65065-183">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="65065-184">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="65065-185">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="65065-186">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="65065-187">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="65065-188">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="65065-189">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="65065-190">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-191">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="65065-192">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="65065-193">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="65065-194">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="65065-195">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="65065-196">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="65065-197">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="65065-198">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="65065-199">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="65065-200">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="65065-201">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="65065-202">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-203">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="65065-204">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-205">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="65065-206">.NET Core 2.0.6 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-206">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="65065-207">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="65065-208">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-208">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="65065-209">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-210">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="65065-211">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-212">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="65065-213">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="65065-214">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="65065-215">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-216">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="65065-217">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="65065-218">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="65065-219">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="65065-220">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="65065-221">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="65065-222">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="65065-223">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="65065-224">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="65065-225">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="65065-226">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="65065-227">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="65065-228">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="65065-229">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="65065-230">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="65065-231">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="65065-232">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="65065-233">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="65065-234">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="65065-235">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="65065-236">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="65065-237">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="65065-238">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="65065-239">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="65065-240">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="65065-241">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="65065-242">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="65065-243">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="65065-244">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="65065-245">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="65065-246">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="65065-247">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="65065-248">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="65065-249">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="65065-250">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="65065-251">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="65065-252">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="65065-253">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="65065-254">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="65065-255">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="65065-256">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="65065-257">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="65065-258">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="65065-259">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-259">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="65065-260">.NET Framework 'den .NET Core 'a serileştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="65065-260">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="65065-261">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-261">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="65065-262">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-262">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="65065-263">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="65065-264">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="65065-265">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="65065-266">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="65065-267">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="65065-268">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="65065-269">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="65065-270">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="65065-271">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="65065-272">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="65065-273">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="65065-274">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="65065-275">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="65065-276">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="65065-277">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="65065-278">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="65065-279">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="65065-280">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="65065-281">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-281">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="65065-282">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="65065-283">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-283">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="65065-284">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="65065-285">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="65065-286">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-286">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="65065-287">Sınırlı serileştirme verileri.</span><span class="sxs-lookup"><span data-stu-id="65065-287">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="65065-288">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-288">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="65065-289">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-289">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="65065-290">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="65065-291">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="65065-292">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="65065-293">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="65065-294">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="65065-295">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="65065-296">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="65065-297">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="65065-298">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="65065-299">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="65065-300">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="65065-301">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="65065-302">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="65065-303">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="65065-304">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="65065-305">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="65065-306">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="65065-307">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="65065-308">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="65065-309">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="65065-310">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="65065-311">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="65065-312">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="65065-313">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="65065-314">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="65065-315">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="65065-316">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="65065-317">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="65065-318">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="65065-319">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="65065-320">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="65065-321">.NET Framework 4,7 ve önceki sürümlerde seri hale getirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="65065-321">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="65065-322">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="65065-323">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-323">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="65065-324">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="65065-325">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="65065-326">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="65065-327">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="65065-328">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="65065-328">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="65065-329">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65065-329">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="65065-330">Serileştirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="65065-330">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="65065-331">[XML ve SOAP serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="65065-331">[XML and SOAP Serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="65065-332">Ortak dil çalışma zamanı ile içerdiği XML serileştirme mekanizması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="65065-332">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="65065-333">[Güvenlik ve serileştirme](../../../docs/framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="65065-333">[Security and Serialization](../../../docs/framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="65065-334">Serileştirme gerçekleştiren kod yazarken izlemek için güvenli kodlama yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="65065-334">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="65065-335">[.NET uzaktan Iletişim](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="65065-335">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="65065-336">Uzak iletişimler için .NET Framework başlayarak çeşitli yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="65065-336">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="65065-337">[ASP.NET ve XML Web hizmeti Istemcileri kullanılarak oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="65065-337">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="65065-338">ASP.NET kullanılarak oluşturulan XML Web hizmetlerinin programlamasını açıklayan ve açıklayan makaleler.</span><span class="sxs-lookup"><span data-stu-id="65065-338">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
