---
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
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990422"
---
# <a name="logging-class"></a><span data-ttu-id="670df-102">Logging sınıfı</span><span class="sxs-lookup"><span data-stu-id="670df-102">Logging class</span></span>

<span data-ttu-id="670df-103">İzleme günlüğü işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="670df-103">Provides trace logging functionality.</span></span>

```csharp
internal class Logging
```

> [!WARNING]
> <span data-ttu-id="670df-104">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="670df-104">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="670df-105">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="670df-105">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="associate-method"></a><span data-ttu-id="670df-106">İlişkilendir yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-106">Associate method</span></span>

<span data-ttu-id="670df-107">İki nesnenin birbirleriyle ilişkilendirildiği bilgileri günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="670df-107">Logs information that two objects are associated with each other.</span></span>

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a><span data-ttu-id="670df-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-108">Parameters</span></span>

- <span data-ttu-id="670df-109">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-109">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-110">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-110">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-111">`objA` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-111">`objA` <xref:System.Object></span></span>

  <span data-ttu-id="670df-112">İle ilişkilendirilecek nesne `objB` .</span><span class="sxs-lookup"><span data-stu-id="670df-112">The object to associate with `objB`.</span></span>

- <span data-ttu-id="670df-113">`objB` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-113">`objB` <xref:System.Object></span></span>

  <span data-ttu-id="670df-114">İle ilişkilendirilecek nesne `objA` .</span><span class="sxs-lookup"><span data-stu-id="670df-114">The object to associate with `objA`.</span></span>

## <a name="entertracesource-object-string-string-method"></a><span data-ttu-id="670df-115">ENTER (TraceSource, Object, String, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-115">Enter(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="670df-116">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="670df-116">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="670df-117">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-117">Parameters</span></span>

- <span data-ttu-id="670df-118">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-118">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-119">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-119">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-120">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-120">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="670df-121">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="670df-121">The object that the method was called on.</span></span>

- <span data-ttu-id="670df-122">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-122">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-123">Girilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-123">The method that is being entered.</span></span>

- <span data-ttu-id="670df-124">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-124">`param` <xref:System.String></span></span>

  <span data-ttu-id="670df-125">Yöntemine geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="670df-125">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-object-string-object-method"></a><span data-ttu-id="670df-126">ENTER (TraceSource, Object, String, Object) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-126">Enter(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="670df-127">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="670df-127">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="670df-128">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-128">Parameters</span></span>

- <span data-ttu-id="670df-129">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-129">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-130">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-130">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-131">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-131">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="670df-132">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="670df-132">The object that the method was called on.</span></span>

- <span data-ttu-id="670df-133">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-133">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-134">Girilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-134">The method that is being entered.</span></span>

- <span data-ttu-id="670df-135">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-135">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="670df-136">Yöntemine geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="670df-136">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-string-method"></a><span data-ttu-id="670df-137">ENTER (TraceSource, String, String, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-137">Enter(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="670df-138">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="670df-138">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="670df-139">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-139">Parameters</span></span>

- <span data-ttu-id="670df-140">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-140">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-141">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-141">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-142">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-142">`obj` <xref:System.String></span></span>

  <span data-ttu-id="670df-143">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="670df-143">The object that the method was called on.</span></span>

- <span data-ttu-id="670df-144">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-144">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-145">Girilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-145">The method that is being entered.</span></span>

- <span data-ttu-id="670df-146">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-146">`param` <xref:System.String></span></span>

  <span data-ttu-id="670df-147">Yöntemine geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="670df-147">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-object-method"></a><span data-ttu-id="670df-148">ENTER (TraceSource, String, String, Object) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-148">Enter(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="670df-149">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="670df-149">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="670df-150">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-150">Parameters</span></span>

- <span data-ttu-id="670df-151">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-151">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-152">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-152">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-153">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-153">`obj` <xref:System.String></span></span>

  <span data-ttu-id="670df-154">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="670df-154">The object that the method was called on.</span></span>

- <span data-ttu-id="670df-155">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-155">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-156">Girilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-156">The method that is being entered.</span></span>

- <span data-ttu-id="670df-157">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-157">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="670df-158">Yöntemine geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="670df-158">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-method"></a><span data-ttu-id="670df-159">ENTER (TraceSource, String, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-159">Enter(TraceSource, string, string) method</span></span>

<span data-ttu-id="670df-160">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="670df-160">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="670df-161">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-161">Parameters</span></span>

- <span data-ttu-id="670df-162">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-162">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-163">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-163">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-164">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-164">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-165">Girilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-165">The method that is being entered.</span></span>

- <span data-ttu-id="670df-166">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-166">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="670df-167">Yöntemine geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="670df-167">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-method"></a><span data-ttu-id="670df-168">ENTER (TraceSource, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-168">Enter(TraceSource, string) method</span></span>

<span data-ttu-id="670df-169">Bir yönteme giriş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="670df-169">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="670df-170">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-170">Parameters</span></span>

- <span data-ttu-id="670df-171">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-171">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-172">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-172">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-173">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-173">`msg` <xref:System.String></span></span>

  <span data-ttu-id="670df-174">İzleme kaynağına kaydedilecek giriş iletisi.</span><span class="sxs-lookup"><span data-stu-id="670df-174">The entrance message to log to the trace source.</span></span>

## <a name="exception-method"></a><span data-ttu-id="670df-175">Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-175">Exception method</span></span>

<span data-ttu-id="670df-176">Bir özel durumu günlüğe kaydeder ve girintiyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="670df-176">Logs an exception and restores indentation.</span></span>

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a><span data-ttu-id="670df-177">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-177">Parameters</span></span>

- <span data-ttu-id="670df-178">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-178">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-179">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-179">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-180">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-180">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="670df-181">Özel durum oluşturan yönteminin çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="670df-181">The object that the method that threw an exception was called on.</span></span>

- <span data-ttu-id="670df-182">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-182">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-183">Özel durumu oluşturan yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-183">The method that threw the exception.</span></span>

- <span data-ttu-id="670df-184">`e` <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="670df-184">`e` <xref:System.Exception></span></span>

  <span data-ttu-id="670df-185">Oluşturulan özel durum.</span><span class="sxs-lookup"><span data-stu-id="670df-185">The exception that was thrown.</span></span>

## <a name="exittracesource-object-string-object-method"></a><span data-ttu-id="670df-186">Exit (TraceSource, nesne, dize, nesne) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-186">Exit(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="670df-187">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="670df-187">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="670df-188">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-188">Parameters</span></span>

- <span data-ttu-id="670df-189">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-189">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-190">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-190">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-191">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-191">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="670df-192">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="670df-192">The object that the method was called on.</span></span>

- <span data-ttu-id="670df-193">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-193">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-194">Çıkılmakta olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-194">The method that is being exited.</span></span>

- <span data-ttu-id="670df-195">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-195">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="670df-196">Yöntemi tarafından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="670df-196">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-object-method"></a><span data-ttu-id="670df-197">Exit (TraceSource, dize, dize, nesne) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-197">Exit(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="670df-198">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="670df-198">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="670df-199">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-199">Parameters</span></span>

- <span data-ttu-id="670df-200">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-200">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-201">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-201">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-202">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-202">`obj` <xref:System.String></span></span>

  <span data-ttu-id="670df-203">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="670df-203">The object that the method was called on.</span></span>

- <span data-ttu-id="670df-204">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-204">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-205">Çıkılmakta olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-205">The method that is being exited.</span></span>

- <span data-ttu-id="670df-206">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-206">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="670df-207">Yöntemi tarafından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="670df-207">The value that's being returned by the method.</span></span>

## <a name="exittracesource-object-string-string-method"></a><span data-ttu-id="670df-208">Exit (TraceSource, Object, String, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-208">Exit(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="670df-209">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="670df-209">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="670df-210">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-210">Parameters</span></span>

- <span data-ttu-id="670df-211">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-211">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-212">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-212">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-213">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="670df-213">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="670df-214">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="670df-214">The object that the method was called on.</span></span>

- <span data-ttu-id="670df-215">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-215">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-216">Çıkılmakta olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-216">The method that is being exited.</span></span>

- <span data-ttu-id="670df-217">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-217">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="670df-218">Yöntemi tarafından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="670df-218">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-string-method"></a><span data-ttu-id="670df-219">Exit (TraceSource, dize, dize, dize) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-219">Exit(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="670df-220">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="670df-220">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="670df-221">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-221">Parameters</span></span>

- <span data-ttu-id="670df-222">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-222">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-223">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-223">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-224">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-224">`obj` <xref:System.String></span></span>

  <span data-ttu-id="670df-225">Metodun çağrıldığı nesne.</span><span class="sxs-lookup"><span data-stu-id="670df-225">The object that the method was called on.</span></span>

- <span data-ttu-id="670df-226">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-226">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-227">Çıkılmakta olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-227">The method that is being exited.</span></span>

- <span data-ttu-id="670df-228">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-228">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="670df-229">Yöntemi tarafından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="670df-229">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-method"></a><span data-ttu-id="670df-230">Exit (TraceSource, dize, dize) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-230">Exit(TraceSource, string, string) method</span></span>

<span data-ttu-id="670df-231">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="670df-231">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="670df-232">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-232">Parameters</span></span>

- <span data-ttu-id="670df-233">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-233">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-234">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-234">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-235">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-235">`method` <xref:System.String></span></span>

  <span data-ttu-id="670df-236">Çıkılmakta olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="670df-236">The method that is being exited.</span></span>

- <span data-ttu-id="670df-237">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-237">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="670df-238">Çıkılmakta olan yönteme geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="670df-238">The parameters that were passed to the method that's being exited.</span></span>

## <a name="exittracesource-string-method"></a><span data-ttu-id="670df-239">Exit (TraceSource, String) yöntemi</span><span class="sxs-lookup"><span data-stu-id="670df-239">Exit(TraceSource, string) method</span></span>

<span data-ttu-id="670df-240">Günlükler bir işlevden çıkış.</span><span class="sxs-lookup"><span data-stu-id="670df-240">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="670df-241">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670df-241">Parameters</span></span>

- <span data-ttu-id="670df-242">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="670df-242">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="670df-243">Olayın günlüğe kaydedilecek izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="670df-243">The trace source to log the event to.</span></span>

- <span data-ttu-id="670df-244">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="670df-244">`msg` <xref:System.String></span></span>

  <span data-ttu-id="670df-245">İzleme kaynağına kaydedilecek çıkış iletisi.</span><span class="sxs-lookup"><span data-stu-id="670df-245">The exit message to log to the trace source.</span></span>

## <a name="http-property"></a><span data-ttu-id="670df-246">Http özelliği</span><span class="sxs-lookup"><span data-stu-id="670df-246">Http property</span></span>

<span data-ttu-id="670df-247">"System .net. http" izleme kaynağını alır.</span><span class="sxs-lookup"><span data-stu-id="670df-247">Gets the trace source for "System.Net.Http".</span></span>

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a><span data-ttu-id="670df-248">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="670df-248">Property value</span></span>

<xref:System.Diagnostics.TraceSource>\
<span data-ttu-id="670df-249">"System .net. http" için izleme kaynağı veya `null` günlüğe kaydetme etkinleştirilmemişse.</span><span class="sxs-lookup"><span data-stu-id="670df-249">The trace source for "System.Net.Http", or `null` if logging is not enabled.</span></span>

## <a name="on-property"></a><span data-ttu-id="670df-250">On özelliği</span><span class="sxs-lookup"><span data-stu-id="670df-250">On property</span></span>

<span data-ttu-id="670df-251">Günlük kaydının etkin olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="670df-251">Gets a value that indicates whether logging is enabled.</span></span>

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a><span data-ttu-id="670df-252">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="670df-252">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="670df-253">`true`günlüğe kaydetme etkinse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="670df-253">`true` if logging is enabled; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="670df-254">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="670df-254">Requirements</span></span>

<span data-ttu-id="670df-255">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="670df-255">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="670df-256">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="670df-256">**Assembly:** System (in System.dll)</span></span>
