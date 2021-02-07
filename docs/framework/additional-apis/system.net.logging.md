---
description: Daha fazla bilgi için bkz. günlük sınıfı
title: Günlük sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 1ae3079ab21502ee3f5bf71db57f0695da9a8571
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726214"
---
# <a name="logging-class"></a><span data-ttu-id="b0af0-103">Logging sınıfı</span><span class="sxs-lookup"><span data-stu-id="b0af0-103">Logging class</span></span>

<span data-ttu-id="b0af0-104">İzleme günlüğü işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0af0-104">Provides trace logging functionality.</span></span>

```csharp
internal class Logging
```

> [!WARNING]
> <span data-ttu-id="b0af0-105">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0af0-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b0af0-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b0af0-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="associate-method"></a><span data-ttu-id="b0af0-107">İlişkilendir yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-107">Associate method</span></span>

<span data-ttu-id="b0af0-108">İki nesnenin birbirleriyle ilişkilendirildiği bilgileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b0af0-108">Logs information that two objects are associated with each other.</span></span>

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-109">Parameters</span></span>

- <span data-ttu-id="b0af0-110">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-110">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-111">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-111">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-112">`objA` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-112">`objA` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-113">İle ilişkilendirilecek nesne `objB` .</span><span class="sxs-lookup"><span data-stu-id="b0af0-113">The object to associate with `objB`.</span></span>

- <span data-ttu-id="b0af0-114">`objB` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-114">`objB` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-115">İle ilişkilendirilecek nesne `objA` .</span><span class="sxs-lookup"><span data-stu-id="b0af0-115">The object to associate with `objA`.</span></span>

## <a name="entertracesource-object-string-string-method"></a><span data-ttu-id="b0af0-116">ENTER (TraceSource, Object, String, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-116">Enter(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="b0af0-117">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b0af0-117">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-118">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-118">Parameters</span></span>

- <span data-ttu-id="b0af0-119">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-119">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-120">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-120">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-121">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-121">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-122">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="b0af0-122">The object that the method was called on.</span></span>

- <span data-ttu-id="b0af0-123">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-123">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-124">Girilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-124">The method that is being entered.</span></span>

- <span data-ttu-id="b0af0-125">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-125">`param` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-126">Yöntemine geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="b0af0-126">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-object-string-object-method"></a><span data-ttu-id="b0af0-127">ENTER (TraceSource, Object, String, Object) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-127">Enter(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="b0af0-128">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b0af0-128">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-129">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-129">Parameters</span></span>

- <span data-ttu-id="b0af0-130">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-130">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-131">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-131">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-132">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-132">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-133">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="b0af0-133">The object that the method was called on.</span></span>

- <span data-ttu-id="b0af0-134">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-134">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-135">Girilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-135">The method that is being entered.</span></span>

- <span data-ttu-id="b0af0-136">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-136">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-137">Yöntemine geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="b0af0-137">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-string-method"></a><span data-ttu-id="b0af0-138">ENTER (TraceSource, String, String, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-138">Enter(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="b0af0-139">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b0af0-139">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-140">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-140">Parameters</span></span>

- <span data-ttu-id="b0af0-141">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-141">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-142">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-142">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-143">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-143">`obj` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-144">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="b0af0-144">The object that the method was called on.</span></span>

- <span data-ttu-id="b0af0-145">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-145">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-146">Girilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-146">The method that is being entered.</span></span>

- <span data-ttu-id="b0af0-147">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-147">`param` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-148">Yöntemine geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="b0af0-148">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-object-method"></a><span data-ttu-id="b0af0-149">ENTER (TraceSource, String, String, Object) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-149">Enter(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="b0af0-150">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b0af0-150">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-151">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-151">Parameters</span></span>

- <span data-ttu-id="b0af0-152">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-152">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-153">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-153">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-154">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-154">`obj` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-155">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="b0af0-155">The object that the method was called on.</span></span>

- <span data-ttu-id="b0af0-156">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-156">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-157">Girilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-157">The method that is being entered.</span></span>

- <span data-ttu-id="b0af0-158">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-158">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-159">Yöntemine geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="b0af0-159">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-method"></a><span data-ttu-id="b0af0-160">ENTER (TraceSource, String, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-160">Enter(TraceSource, string, string) method</span></span>

<span data-ttu-id="b0af0-161">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b0af0-161">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-162">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-162">Parameters</span></span>

- <span data-ttu-id="b0af0-163">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-163">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-164">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-164">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-165">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-165">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-166">Girilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-166">The method that is being entered.</span></span>

- <span data-ttu-id="b0af0-167">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-167">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-168">Yöntemine geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="b0af0-168">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-method"></a><span data-ttu-id="b0af0-169">ENTER (TraceSource, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-169">Enter(TraceSource, string) method</span></span>

<span data-ttu-id="b0af0-170">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b0af0-170">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-171">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-171">Parameters</span></span>

- <span data-ttu-id="b0af0-172">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-172">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-173">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-173">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-174">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-174">`msg` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-175">İzleme kaynağına kaydedilecek giriş iletisi.</span><span class="sxs-lookup"><span data-stu-id="b0af0-175">The entrance message to log to the trace source.</span></span>

## <a name="exception-method"></a><span data-ttu-id="b0af0-176">Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-176">Exception method</span></span>

<span data-ttu-id="b0af0-177">Bir özel durumu günlüğe kaydeder ve girintiyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="b0af0-177">Logs an exception and restores indentation.</span></span>

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-178">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-178">Parameters</span></span>

- <span data-ttu-id="b0af0-179">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-179">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-180">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-180">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-181">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-181">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-182">Özel durum oluşturan yönteminin çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="b0af0-182">The object that the method that threw an exception was called on.</span></span>

- <span data-ttu-id="b0af0-183">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-183">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-184">Özel durumu oluşturan yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-184">The method that threw the exception.</span></span>

- <span data-ttu-id="b0af0-185">`e` <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="b0af0-185">`e` <xref:System.Exception></span></span>

  <span data-ttu-id="b0af0-186">Oluşturulan özel durum.</span><span class="sxs-lookup"><span data-stu-id="b0af0-186">The exception that was thrown.</span></span>

## <a name="exittracesource-object-string-object-method"></a><span data-ttu-id="b0af0-187">Exit (TraceSource, nesne, dize, nesne) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-187">Exit(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="b0af0-188">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="b0af0-188">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-189">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-189">Parameters</span></span>

- <span data-ttu-id="b0af0-190">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-190">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-191">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-191">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-192">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-192">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-193">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="b0af0-193">The object that the method was called on.</span></span>

- <span data-ttu-id="b0af0-194">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-194">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-195">Çıkılmakta olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-195">The method that is being exited.</span></span>

- <span data-ttu-id="b0af0-196">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-196">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-197">Yöntemi tarafından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="b0af0-197">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-object-method"></a><span data-ttu-id="b0af0-198">Exit (TraceSource, dize, dize, nesne) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-198">Exit(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="b0af0-199">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="b0af0-199">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-200">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-200">Parameters</span></span>

- <span data-ttu-id="b0af0-201">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-201">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-202">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-202">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-203">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-203">`obj` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-204">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="b0af0-204">The object that the method was called on.</span></span>

- <span data-ttu-id="b0af0-205">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-205">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-206">Çıkılmakta olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-206">The method that is being exited.</span></span>

- <span data-ttu-id="b0af0-207">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-207">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-208">Yöntemi tarafından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="b0af0-208">The value that's being returned by the method.</span></span>

## <a name="exittracesource-object-string-string-method"></a><span data-ttu-id="b0af0-209">Exit (TraceSource, Object, String, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-209">Exit(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="b0af0-210">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="b0af0-210">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-211">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-211">Parameters</span></span>

- <span data-ttu-id="b0af0-212">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-212">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-213">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-213">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-214">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b0af0-214">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="b0af0-215">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="b0af0-215">The object that the method was called on.</span></span>

- <span data-ttu-id="b0af0-216">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-216">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-217">Çıkılmakta olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-217">The method that is being exited.</span></span>

- <span data-ttu-id="b0af0-218">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-218">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-219">Yöntemi tarafından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="b0af0-219">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-string-method"></a><span data-ttu-id="b0af0-220">Exit (TraceSource, dize, dize, dize) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-220">Exit(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="b0af0-221">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="b0af0-221">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-222">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-222">Parameters</span></span>

- <span data-ttu-id="b0af0-223">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-223">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-224">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-224">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-225">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-225">`obj` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-226">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="b0af0-226">The object that the method was called on.</span></span>

- <span data-ttu-id="b0af0-227">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-227">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-228">Çıkılmakta olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-228">The method that is being exited.</span></span>

- <span data-ttu-id="b0af0-229">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-229">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-230">Yöntemi tarafından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="b0af0-230">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-method"></a><span data-ttu-id="b0af0-231">Exit (TraceSource, dize, dize) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-231">Exit(TraceSource, string, string) method</span></span>

<span data-ttu-id="b0af0-232">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="b0af0-232">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-233">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-233">Parameters</span></span>

- <span data-ttu-id="b0af0-234">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-234">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-235">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-235">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-236">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-236">`method` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-237">Çıkılmakta olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="b0af0-237">The method that is being exited.</span></span>

- <span data-ttu-id="b0af0-238">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-238">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-239">Çıkılmakta olan yönteme geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="b0af0-239">The parameters that were passed to the method that's being exited.</span></span>

## <a name="exittracesource-string-method"></a><span data-ttu-id="b0af0-240">Exit (TraceSource, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0af0-240">Exit(TraceSource, string) method</span></span>

<span data-ttu-id="b0af0-241">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="b0af0-241">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="b0af0-242">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0af0-242">Parameters</span></span>

- <span data-ttu-id="b0af0-243">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b0af0-243">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b0af0-244">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b0af0-244">The trace source to log the event to.</span></span>

- <span data-ttu-id="b0af0-245">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b0af0-245">`msg` <xref:System.String></span></span>

  <span data-ttu-id="b0af0-246">İzleme kaynağına kaydedilecek çıkış iletisi.</span><span class="sxs-lookup"><span data-stu-id="b0af0-246">The exit message to log to the trace source.</span></span>

## <a name="http-property"></a><span data-ttu-id="b0af0-247">Http özelliği</span><span class="sxs-lookup"><span data-stu-id="b0af0-247">Http property</span></span>

<span data-ttu-id="b0af0-248">"System .net. http" izleme kaynağını alır.</span><span class="sxs-lookup"><span data-stu-id="b0af0-248">Gets the trace source for "System.Net.Http".</span></span>

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a><span data-ttu-id="b0af0-249">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="b0af0-249">Property value</span></span>

<xref:System.Diagnostics.TraceSource>\
<span data-ttu-id="b0af0-250">"System .net. http" için izleme kaynağı veya `null` günlüğe kaydetme etkinleştirilmemişse.</span><span class="sxs-lookup"><span data-stu-id="b0af0-250">The trace source for "System.Net.Http", or `null` if logging is not enabled.</span></span>

## <a name="on-property"></a><span data-ttu-id="b0af0-251">On özelliği</span><span class="sxs-lookup"><span data-stu-id="b0af0-251">On property</span></span>

<span data-ttu-id="b0af0-252">Günlük kaydının etkin olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b0af0-252">Gets a value that indicates whether logging is enabled.</span></span>

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a><span data-ttu-id="b0af0-253">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="b0af0-253">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="b0af0-254">`true` günlüğe kaydetme etkinse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="b0af0-254">`true` if logging is enabled; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0af0-255">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0af0-255">Requirements</span></span>

<span data-ttu-id="b0af0-256">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="b0af0-256">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="b0af0-257">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="b0af0-257">**Assembly:** System (in System.dll)</span></span>
