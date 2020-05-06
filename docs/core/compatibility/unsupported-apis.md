---
title: .NET Core 'da desteklenmeyen API 'Ler
titleSuffix: ''
description: .NET Core üzerinde her zaman bir özel durum oluşturan .NET Framework hangi API 'Leri öğrenin.
ms.date: 12/23/2019
ms.openlocfilehash: 941e9149c7679afe4a888149108d0a9a28e5e7ab
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794604"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="e917e-103">.NET Core üzerinde her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="e917e-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="e917e-104">Aşağıdaki API 'Ler her zaman bir <xref:System.PlatformNotSupportedException> platform alt kümesi üzerinde .NET Core üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e917e-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="e917e-105">Bu makale, etkilenen API üyelerini ad alanına göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="e917e-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="e917e-106">Bu makale, devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="e917e-106">This article is a work-in-progress.</span></span> <span data-ttu-id="e917e-107">.NET Core üzerinde özel durum oluşturan API 'lerin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="e917e-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="e917e-108">Bu makale, .NET Core üzerinde throw ikili serileştirme için açık arabirim uygulamaları içermez.</span><span class="sxs-lookup"><span data-stu-id="e917e-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="e917e-109">Daha fazla bilgi için bkz. [.NET Core 'Da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="e917e-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="e917e-110">Sistem</span><span class="sxs-lookup"><span data-stu-id="e917e-110">System</span></span>

| <span data-ttu-id="e917e-111">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-111">Member</span></span> | <span data-ttu-id="e917e-112">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-113">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="e917e-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="e917e-115">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="e917e-116">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="e917e-118">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="e917e-119">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="e917e-120">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-121">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e917e-122">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="e917e-123">System. CodeDom. derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e917e-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="e917e-124">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-124">Member</span></span> | <span data-ttu-id="e917e-125">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-127">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-128">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="e917e-129">System. Collections. özelleşmiş</span><span class="sxs-lookup"><span data-stu-id="e917e-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="e917e-130">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-130">Member</span></span> | <span data-ttu-id="e917e-131">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-132">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e917e-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="e917e-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="e917e-135">System.Configuration</span></span>

| <span data-ttu-id="e917e-136">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-136">Member</span></span> | <span data-ttu-id="e917e-137">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e917e-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="e917e-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="e917e-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="e917e-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="e917e-140">System.Console</span></span>

| <span data-ttu-id="e917e-141">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-141">Member</span></span> | <span data-ttu-id="e917e-142">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="e917e-143">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-143">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-145">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-145">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-147">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-147">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-149">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-149">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="e917e-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e917e-151">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-152">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-153">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-154">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-154">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-155"><xref:System.Console.Title?displayProperty=nameWithType>(yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="e917e-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e917e-156">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-156">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-158">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-158">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-160">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-160">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-162">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-162">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-164">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="e917e-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="e917e-165">System.Data.Common</span></span>

| <span data-ttu-id="e917e-166">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-166">Member</span></span> | <span data-ttu-id="e917e-167">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e917e-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(atar <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="e917e-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="e917e-169">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="e917e-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="e917e-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="e917e-171">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-171">Member</span></span> | <span data-ttu-id="e917e-172">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e917e-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-174">Linux</span><span class="sxs-lookup"><span data-stu-id="e917e-174">Linux</span></span> |
| <span data-ttu-id="e917e-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-176">Linux</span><span class="sxs-lookup"><span data-stu-id="e917e-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="e917e-177">macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="e917e-178">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-179">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="e917e-180">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="e917e-181">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="e917e-182">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="e917e-183">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-183">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-185">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-185">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="e917e-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e917e-187">Mac OS</span><span class="sxs-lookup"><span data-stu-id="e917e-187">macOS</span></span> |
| <span data-ttu-id="e917e-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-189">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="e917e-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="e917e-190">System.IO</span></span>

| <span data-ttu-id="e917e-191">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-191">Member</span></span> | <span data-ttu-id="e917e-192">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-193">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-194">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="e917e-195">System. ıO. Pipes</span><span class="sxs-lookup"><span data-stu-id="e917e-195">System.IO.Pipes</span></span>

| <span data-ttu-id="e917e-196">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-196">Member</span></span> | <span data-ttu-id="e917e-197">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="e917e-198">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="e917e-199">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="e917e-200">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="e917e-201">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-201">Linux and macOS</span></span> |
| <span data-ttu-id="e917e-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-203">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="e917e-204">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="e917e-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="e917e-205">System.Media</span></span>

| <span data-ttu-id="e917e-206">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-206">Member</span></span> | <span data-ttu-id="e917e-207">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-208">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="e917e-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="e917e-209">System.Net</span></span>

| <span data-ttu-id="e917e-210">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-210">Member</span></span> | <span data-ttu-id="e917e-211">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="e917e-212">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="e917e-213">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-214">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-215">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-216">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-217">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-218">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-219">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-220">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-221">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-222">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="e917e-223">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-224">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-225">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-226">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-227">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-228">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="e917e-229">System .net. NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="e917e-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="e917e-230">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-230">Member</span></span> | <span data-ttu-id="e917e-231">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="e917e-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="e917e-233">System .net. Sockets</span><span class="sxs-lookup"><span data-stu-id="e917e-233">System.Net.Sockets</span></span>

| <span data-ttu-id="e917e-234">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-234">Member</span></span> | <span data-ttu-id="e917e-235">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="e917e-236">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="e917e-237">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="e917e-238">System .net. WebSockets</span><span class="sxs-lookup"><span data-stu-id="e917e-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="e917e-239">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-239">Member</span></span> | <span data-ttu-id="e917e-240">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="e917e-241">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="e917e-242">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="e917e-242">System.Reflection</span></span>

| <span data-ttu-id="e917e-243">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-243">Member</span></span> | <span data-ttu-id="e917e-244">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-245">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e917e-246">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-247">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e917e-248">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="e917e-249">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-250">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="e917e-251">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="e917e-252">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="e917e-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="e917e-253">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-253">Member</span></span> | <span data-ttu-id="e917e-254">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="e917e-255">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="e917e-256">System. Runtime. InteropServices</span><span class="sxs-lookup"><span data-stu-id="e917e-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="e917e-257">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-257">Member</span></span> | <span data-ttu-id="e917e-258">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e917e-259">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="e917e-260">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="e917e-261">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="e917e-262">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e917e-263">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="e917e-264">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="e917e-265">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="e917e-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="e917e-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="e917e-267">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-267">Member</span></span> | <span data-ttu-id="e917e-268">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="e917e-269">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="e917e-270">System. Security</span><span class="sxs-lookup"><span data-stu-id="e917e-270">System.Security</span></span>

| <span data-ttu-id="e917e-271">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-271">Member</span></span> | <span data-ttu-id="e917e-272">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="e917e-273">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="e917e-274">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="e917e-275">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="e917e-276">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="e917e-277">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="e917e-278">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="e917e-279">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="e917e-280">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="e917e-281">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="e917e-282">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="e917e-283">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e917e-284">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="e917e-285">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="e917e-286">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="e917e-287">System. Security. Claim</span><span class="sxs-lookup"><span data-stu-id="e917e-287">System.Security.Claims</span></span>

| <span data-ttu-id="e917e-288">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-288">Member</span></span> | <span data-ttu-id="e917e-289">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="e917e-290">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-291">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="e917e-292">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-293">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-294">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="e917e-295">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="e917e-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="e917e-296">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-296">Member</span></span> | <span data-ttu-id="e917e-297">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e917e-298">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="e917e-299">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="e917e-300">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="e917e-301">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="e917e-302">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="e917e-303">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="e917e-304">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="e917e-305">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="e917e-306">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="e917e-307">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="e917e-308">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="e917e-309">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="e917e-310">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="e917e-311">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e917e-312">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="e917e-313">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e917e-314">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-315">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-316">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-317">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e917e-318">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e917e-319">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-320">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-321">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="e917e-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-322">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-323">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e917e-324">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e917e-325">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="e917e-326">System. Security. Cryptography. Pkcs</span><span class="sxs-lookup"><span data-stu-id="e917e-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="e917e-327">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-327">Member</span></span> | <span data-ttu-id="e917e-328">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="e917e-329">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e917e-330">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="e917e-331">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="e917e-332">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="e917e-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="e917e-333">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-333">Member</span></span> | <span data-ttu-id="e917e-334">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-335">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-336">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-337">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-337">All</span></span> |
| <span data-ttu-id="e917e-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="e917e-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e917e-339">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="e917e-340">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="e917e-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="e917e-341">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-341">Member</span></span> | <span data-ttu-id="e917e-342">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-343">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="e917e-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="e917e-344">System.Security.Policy</span></span>

| <span data-ttu-id="e917e-345">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-345">Member</span></span> | <span data-ttu-id="e917e-346">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-347">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="e917e-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="e917e-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="e917e-349">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-349">Member</span></span> | <span data-ttu-id="e917e-350">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e917e-351">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="e917e-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="e917e-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="e917e-353">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-353">Member</span></span> | <span data-ttu-id="e917e-354">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-355">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="e917e-356">System. Threading</span><span class="sxs-lookup"><span data-stu-id="e917e-356">System.Threading</span></span>

| <span data-ttu-id="e917e-357">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-357">Member</span></span> | <span data-ttu-id="e917e-358">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-359">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e917e-360">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="e917e-361">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="e917e-362">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="e917e-363">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="e917e-364">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="e917e-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="e917e-365">System.Xml</span></span>

| <span data-ttu-id="e917e-366">Üye</span><span class="sxs-lookup"><span data-stu-id="e917e-366">Member</span></span> | <span data-ttu-id="e917e-367">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="e917e-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="e917e-368">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="e917e-369">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e917e-370">Tümü</span><span class="sxs-lookup"><span data-stu-id="e917e-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="e917e-371">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e917e-371">See also</span></span>

- [<span data-ttu-id="e917e-372">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="e917e-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="e917e-373">.NET Core 'da ikili serileştirme</span><span class="sxs-lookup"><span data-stu-id="e917e-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="e917e-374">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="e917e-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
