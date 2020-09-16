---
title: İkili serileştirme
description: Bu makalede, .NET Core 'un desteklediği ikili serileştirme ve türler açıklanır. İkili serileştirme ve alternatiflerin tehlikeleri hakkında farkında olun.
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
ms.openlocfilehash: 2ede74dd8a48735a7ded450d1da6d9cda8fc5ae6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554501"
---
# <a name="binary-serialization"></a><span data-ttu-id="a9c7e-104">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="a9c7e-104">Binary serialization</span></span>

<span data-ttu-id="a9c7e-105">Serileştirme depolama ortamına bir nesne durumunu depolama işlemi olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-105">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="a9c7e-106">Bu işlem sırasında, nesnenin ortak ve özel alanları ile sınıfın adı, sınıfı içeren derleme dahil olmak üzere, bir veri akışına yazılan bayt akışına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-106">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="a9c7e-107">Nesnenin seri durumdan daha sonra orijinal nesneyi tam bir kopyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-107">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="a9c7e-108">Bir serileştirme mekanizmasını nesne yönelimli bir ortamda uygularken, kullanım kolaylığı ve esneklik arasında bir dizi denge yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-108">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="a9c7e-109">Süreç üzerinde yeterli denetim verildiğinden işlem, büyük bir ölçüde otomatik olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-109">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="a9c7e-110">Örneğin, burada basit ikili serileştirme yeterli değil veya bir sınıf hangi alanları seri hale gerek karar vermek için belirli bir neden olabilir durumlarda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-110">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="a9c7e-111">Aşağıdaki bölümlerde .NET ile sunulan güçlü serileştirme mekanizması incelenecektir ve bu işlemi gereksinimlerinizi karşılayacak şekilde özelleştirmenize imkan tanıyan bazı önemli özellikler vurgulanacak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-111">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="a9c7e-112">Nesnenin serileştirildiği ve farklı .NET Framework sürümleri kullanılarak seri durumdan UTF-8 veya UTF-7 kodlanmış nesne durumunu korunur değil.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-112">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="a9c7e-113">İkili serileştirme bir nesne içindeki özel üyelerin değiştirilmesini ve bu nedenle durumunun değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-113">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="a9c7e-114">Bu nedenle, <xref:System.Text.Json?displayProperty=fullName> ortak API yüzeyinde çalışan gibi diğer serileştirme çerçeveleri önerilir.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-114">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="a9c7e-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a9c7e-115">.NET Core</span></span>

<span data-ttu-id="a9c7e-116">.NET Core bir tür alt kümesi için ikili serileştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-116">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="a9c7e-117">Desteklenen türlerin listesini aşağıdaki [seri hale getirilebilir türler](#serializable-types) bölümünde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-117">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="a9c7e-118">Listelenen türlerin .NET Framework 4.5.1 ve sonraki sürümleri ile .NET Core 2,0 ve sonraki sürümleri arasında seri hale getirilebilir olduğu garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-118">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="a9c7e-119">Mono gibi diğer .NET uygulamaları resmi olarak desteklenmez, ancak aynı zamanda çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-119">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="a9c7e-120">Serileştirilebilir türler</span><span class="sxs-lookup"><span data-stu-id="a9c7e-120">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="a9c7e-121">Tür</span><span class="sxs-lookup"><span data-stu-id="a9c7e-121">Type</span></span> | <span data-ttu-id="a9c7e-122">Notlar</span><span class="sxs-lookup"><span data-stu-id="a9c7e-122">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-123">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-124">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-125">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-126">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-127">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-128">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-129">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-130">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-131">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-132">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-133">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-134">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-134">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-135">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-136">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-136">Starting in .NET Core 2.0.4.</span></span> |
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
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="a9c7e-137">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-138">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-139">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-140">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-140">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-141">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-141">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-142">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-142">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="a9c7e-143">.NET Framework 'den .NET Core 'a serileştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-143">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-144">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-145">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-146">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-147">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-148">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-149">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-150">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-151">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-151">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-152">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-153">.NET Core 2.0.2 ve sonraki sürümlerde başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-153">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-154">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-155">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-156">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-156">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-157">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-158">' A ayarlarsanız `RemotingFormat` `SerializationFormat.Binary` , yalnızca .net Core 2,1 ve sonraki sürümlerle değiş tokuş edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-158">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-159">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-160">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-161">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-162">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-163">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-164">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-165">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-166">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-167">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-168">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-169">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-169">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-170">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-170">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-171">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-171">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="a9c7e-172">.NET Framework 'den .NET Core 'a serileştirme desteklenmez</span><span class="sxs-lookup"><span data-stu-id="a9c7e-172">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-173">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-174">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-175">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-176">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-177">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-178">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-179">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-180">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-181">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="a9c7e-182">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-183">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-184">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-185">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-186">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-187">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-188">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-189">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-190">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-191">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-192">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-193">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-194">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-195">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-196">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-197">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-198">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-199">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-200">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-201">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-202">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-203">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-204">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-205">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-206">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-206">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-207">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-208">.NET Core 2.0.6 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-208">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-209">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-210">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-211">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-212">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="a9c7e-213">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-214">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-215">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-216">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-217">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-218">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-219">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-220">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-221">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-222">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-223">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-224">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-225">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-226">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-227">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-228">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-229">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-230">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-231">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-232">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-233">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-234">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-235">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-236">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-237">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-238">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-239">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-240">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-241">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-242">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-243">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-244">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-245">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-246">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-247">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-248">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-249">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-250">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-251">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-252">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-253">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-254">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-255">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-256">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-257">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-258">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-259">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-259">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-260">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-260">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-261">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-261">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="a9c7e-262">.NET Framework 'den .NET Core 'a serileştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-262">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-263">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-264">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-265">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-266">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-267">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-268">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-269">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-270">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-271">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-272">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-273">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-274">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-275">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-276">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-277">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-278">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-279">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-280">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-281">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-281">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-282">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-283">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-283">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="a9c7e-284">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-285">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-286">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-286">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-287">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-287">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-288">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-288">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="a9c7e-289">Sınırlı serileştirme verileri.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-289">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-290">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-291">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-292">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-293">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-294">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-295">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-296">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-297">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-298">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-299">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-300">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-301">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-302">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-303">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-304">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-305">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-306">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-307">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-308">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-309">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-310">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-311">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-312">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-313">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-314">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-315">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-316">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-317">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-318">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-319">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-320">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-321">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-321">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-322">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-323">.NET Framework 4,7 ve önceki sürümlerde seri hale getirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-323">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-324">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-325">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-326">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-327">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-328">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-328">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-329">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-329">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="a9c7e-330">.NET Core 2.0.4 'tan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-330">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="a9c7e-331">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-331">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="a9c7e-332">Serileştirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-332">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="a9c7e-333">[XML ve SOAP serileştirme](xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="a9c7e-333">[XML and SOAP Serialization](xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="a9c7e-334">Ortak dil çalışma zamanı ile içerdiği XML serileştirme mekanizması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-334">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="a9c7e-335">[Güvenlik ve serileştirme](../../framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="a9c7e-335">[Security and Serialization](../../framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="a9c7e-336">Serileştirme gerçekleştiren kod yazarken izlemek için güvenli kodlama yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-336">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="a9c7e-337">[.NET uzaktan Iletişim](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9c7e-337">[.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="a9c7e-338">Uzak iletişimler için .NET Framework başlayarak çeşitli yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-338">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="a9c7e-339">[ASP.NET ve XML Web hizmeti Istemcileri kullanılarak oluşturulan XML Web Hizmetleri](/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9c7e-339">[XML Web Services Created Using ASP.NET and XML Web Service Clients](/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="a9c7e-340">ASP.NET kullanılarak oluşturulan XML Web hizmetlerinin programlamasını açıklayan ve açıklayan makaleler.</span><span class="sxs-lookup"><span data-stu-id="a9c7e-340">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
