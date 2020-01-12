---
title: .NET Core 'da desteklenmeyen API 'Ler
description: .NET Core üzerinde her zaman bir özel durum oluşturan .NET Framework hangi API 'Leri öğrenin.
ms.date: 12/23/2019
ms.openlocfilehash: 0cb533f10d53fd3d287265032e3de13c242a8ae0
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901497"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="864d2-103">.NET Core üzerinde her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="864d2-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="864d2-104">Aşağıdaki API 'Ler, belirtilen platformda .NET Core üzerinde çalıştırıldığında her zaman bir <xref:System.PlatformNotSupportedException> aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="864d2-104">The following APIs will always through a <xref:System.PlatformNotSupportedException> when run on .NET Core on the specified platform.</span></span>

<span data-ttu-id="864d2-105">Bu makale, etkilenen API üyelerini ad alanına göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="864d2-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="864d2-106">Bu makale, devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="864d2-106">This article is a work-in-progress.</span></span> <span data-ttu-id="864d2-107">.NET Core üzerinde özel durum oluşturan API 'lerin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="864d2-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="864d2-108">Bu makale, .NET Core üzerinde throw ikili serileştirme için açık arabirim uygulamaları içermez.</span><span class="sxs-lookup"><span data-stu-id="864d2-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="864d2-109">Daha fazla bilgi için bkz. [.NET Core 'Da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="864d2-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="864d2-110">Sistem</span><span class="sxs-lookup"><span data-stu-id="864d2-110">System</span></span>

| <span data-ttu-id="864d2-111">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-111">Member</span></span> | <span data-ttu-id="864d2-112">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-112">Platform</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-113">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="864d2-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="864d2-115">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="864d2-116">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="864d2-118">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="864d2-119">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="864d2-120">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-121">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="864d2-122">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="864d2-123">System. CodeDom. derleyicisi</span><span class="sxs-lookup"><span data-stu-id="864d2-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="864d2-124">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-124">Member</span></span> | <span data-ttu-id="864d2-125">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-125">Platform</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-127">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-128">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="864d2-129">System. Collections. özelleşmiş</span><span class="sxs-lookup"><span data-stu-id="864d2-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="864d2-130">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-130">Member</span></span> | <span data-ttu-id="864d2-131">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-131">Platform</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-132">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="864d2-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="864d2-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="864d2-135">System.Configuration</span></span>

| <span data-ttu-id="864d2-136">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-136">Member</span></span> | <span data-ttu-id="864d2-137">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-137">Platform</span></span> |
| - | - |
| <span data-ttu-id="864d2-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="864d2-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="864d2-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="864d2-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="864d2-140">System.Console</span></span>

| <span data-ttu-id="864d2-141">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-141">Member</span></span> | <span data-ttu-id="864d2-142">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-142">Platform</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="864d2-143">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-143">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-145">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-145">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-147">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-147">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-149">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-149">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="864d2-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="864d2-151">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-152">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-153">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-154">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-154">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-155"><xref:System.Console.Title?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="864d2-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="864d2-156">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-156">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-158">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-158">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-160">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-160">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-162">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-162">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-164">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="864d2-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="864d2-165">System.Data.Common</span></span>

| <span data-ttu-id="864d2-166">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-166">Member</span></span> | <span data-ttu-id="864d2-167">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-167">Platform</span></span> |
| - | - |
| <span data-ttu-id="864d2-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (<xref:System.NotSupportedException>oluşturur)</span><span class="sxs-lookup"><span data-stu-id="864d2-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="864d2-169">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="864d2-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="864d2-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="864d2-171">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-171">Member</span></span> | <span data-ttu-id="864d2-172">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-172">Platform</span></span> |
| - | - |
| <span data-ttu-id="864d2-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-174">Linux</span><span class="sxs-lookup"><span data-stu-id="864d2-174">Linux</span></span> |
| <span data-ttu-id="864d2-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-176">Linux</span><span class="sxs-lookup"><span data-stu-id="864d2-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="864d2-177">macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="864d2-178">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-179">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="864d2-180">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="864d2-181">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="864d2-182">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="864d2-183">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-183">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-185">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-185">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="864d2-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="864d2-187">macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-187">macOS</span></span> |
| <span data-ttu-id="864d2-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-189">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="864d2-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="864d2-190">System.IO</span></span>

| <span data-ttu-id="864d2-191">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-191">Member</span></span> | <span data-ttu-id="864d2-192">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-192">Platform</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-193">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-194">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="864d2-195">System. ıO. Pipes</span><span class="sxs-lookup"><span data-stu-id="864d2-195">System.IO.Pipes</span></span>

| <span data-ttu-id="864d2-196">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-196">Member</span></span> | <span data-ttu-id="864d2-197">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-197">Platform</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="864d2-198">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="864d2-199">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="864d2-200">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="864d2-201">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-201">Linux and macOS</span></span> |
| <span data-ttu-id="864d2-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-203">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="864d2-204">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="864d2-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="864d2-205">System.Media</span></span>

| <span data-ttu-id="864d2-206">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-206">Member</span></span> | <span data-ttu-id="864d2-207">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-207">Platform</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-208">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="864d2-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="864d2-209">System.Net</span></span>

| <span data-ttu-id="864d2-210">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-210">Member</span></span> | <span data-ttu-id="864d2-211">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-211">Platform</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="864d2-212">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="864d2-213">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-214">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-215">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-216">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-217">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-218">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-219">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-220">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-221">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-222">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="864d2-223">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-224">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-225">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-226">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-227">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-228">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="864d2-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="864d2-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="864d2-230">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-230">Member</span></span> | <span data-ttu-id="864d2-231">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-231">Platform</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="864d2-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="864d2-233">System .net. Sockets</span><span class="sxs-lookup"><span data-stu-id="864d2-233">System.Net.Sockets</span></span>

| <span data-ttu-id="864d2-234">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-234">Member</span></span> | <span data-ttu-id="864d2-235">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-235">Platform</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="864d2-236">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-236">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="864d2-237">System .net. WebSockets</span><span class="sxs-lookup"><span data-stu-id="864d2-237">System.Net.WebSockets</span></span>

| <span data-ttu-id="864d2-238">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-238">Member</span></span> | <span data-ttu-id="864d2-239">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-239">Platform</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="864d2-240">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-240">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="864d2-241">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="864d2-241">System.Reflection</span></span>

| <span data-ttu-id="864d2-242">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-242">Member</span></span> | <span data-ttu-id="864d2-243">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-243">Platform</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-244">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-244">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="864d2-245">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-245">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-246">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="864d2-247">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-247">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="864d2-248">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-249">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="864d2-250">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-250">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="864d2-251">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="864d2-251">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="864d2-252">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-252">Member</span></span> | <span data-ttu-id="864d2-253">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-253">Platform</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="864d2-254">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-254">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="864d2-255">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="864d2-255">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="864d2-256">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-256">Member</span></span> | <span data-ttu-id="864d2-257">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-257">Platform</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="864d2-258">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-258">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="864d2-259">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="864d2-260">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="864d2-261">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-261">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="864d2-262">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-262">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="864d2-263">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="864d2-264">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-264">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="864d2-265">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="864d2-265">System.Runtime.Serialization</span></span>

| <span data-ttu-id="864d2-266">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-266">Member</span></span> | <span data-ttu-id="864d2-267">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-267">Platform</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="864d2-268">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-268">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="864d2-269">System. Security</span><span class="sxs-lookup"><span data-stu-id="864d2-269">System.Security</span></span>

| <span data-ttu-id="864d2-270">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-270">Member</span></span> | <span data-ttu-id="864d2-271">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-271">Platform</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="864d2-272">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-272">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="864d2-273">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-273">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="864d2-274">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-274">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="864d2-275">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-275">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="864d2-276">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-276">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="864d2-277">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-277">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="864d2-278">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-278">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="864d2-279">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-279">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="864d2-280">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="864d2-281">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-281">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="864d2-282">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-282">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="864d2-283">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-283">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="864d2-284">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="864d2-285">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-285">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="864d2-286">System. Security. Claim</span><span class="sxs-lookup"><span data-stu-id="864d2-286">System.Security.Claims</span></span>

| <span data-ttu-id="864d2-287">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-287">Member</span></span> | <span data-ttu-id="864d2-288">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-288">Platform</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="864d2-289">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-289">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-290">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="864d2-291">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-292">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-293">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-293">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="864d2-294">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="864d2-294">System.Security.Cryptography</span></span>

| <span data-ttu-id="864d2-295">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-295">Member</span></span> | <span data-ttu-id="864d2-296">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-296">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="864d2-297">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-297">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-298">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-298">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="864d2-299">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="864d2-300">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="864d2-301">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="864d2-302">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="864d2-303">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="864d2-304">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="864d2-305">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="864d2-306">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="864d2-307">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="864d2-308">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="864d2-309">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="864d2-310">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="864d2-311">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-311">All</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="864d2-312">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="864d2-313">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="864d2-314">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-315">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-316">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-317">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="864d2-318">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="864d2-319">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-320">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-321">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="864d2-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-322">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-323">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="864d2-324">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="864d2-325">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="864d2-326">System. Security. Cryptography. Pkcs</span><span class="sxs-lookup"><span data-stu-id="864d2-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="864d2-327">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-327">Member</span></span> | <span data-ttu-id="864d2-328">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-328">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="864d2-329">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="864d2-330">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="864d2-331">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="864d2-332">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="864d2-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="864d2-333">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-333">Member</span></span> | <span data-ttu-id="864d2-334">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-334">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-335">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-336">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-337">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-337">All</span></span> |
| <span data-ttu-id="864d2-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="864d2-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="864d2-339">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="864d2-340">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="864d2-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="864d2-341">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-341">Member</span></span> | <span data-ttu-id="864d2-342">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-342">Platform</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-343">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="864d2-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="864d2-344">System.Security.Policy</span></span>

| <span data-ttu-id="864d2-345">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-345">Member</span></span> | <span data-ttu-id="864d2-346">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-346">Platform</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-347">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="864d2-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="864d2-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="864d2-349">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-349">Member</span></span> | <span data-ttu-id="864d2-350">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-350">Platform</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-351">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="864d2-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="864d2-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="864d2-353">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-353">Member</span></span> | <span data-ttu-id="864d2-354">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-354">Platform</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-355">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="864d2-356">System. Threading</span><span class="sxs-lookup"><span data-stu-id="864d2-356">System.Threading</span></span>

| <span data-ttu-id="864d2-357">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-357">Member</span></span> | <span data-ttu-id="864d2-358">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-358">Platform</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-359">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="864d2-360">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="864d2-361">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="864d2-362">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="864d2-363">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="864d2-364">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="864d2-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="864d2-365">System.Xml</span></span>

| <span data-ttu-id="864d2-366">Üye</span><span class="sxs-lookup"><span data-stu-id="864d2-366">Member</span></span> | <span data-ttu-id="864d2-367">Platform</span><span class="sxs-lookup"><span data-stu-id="864d2-367">Platform</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="864d2-368">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="864d2-369">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="864d2-370">Tümü</span><span class="sxs-lookup"><span data-stu-id="864d2-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="864d2-371">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="864d2-371">See also</span></span>

- [<span data-ttu-id="864d2-372">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="864d2-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="864d2-373">.NET Core 'da ikili serileştirme</span><span class="sxs-lookup"><span data-stu-id="864d2-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="864d2-374">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="864d2-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
