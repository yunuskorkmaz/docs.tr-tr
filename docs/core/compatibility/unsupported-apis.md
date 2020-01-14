---
title: .NET Core 'da desteklenmeyen API 'Ler
description: .NET Core üzerinde her zaman bir özel durum oluşturan .NET Framework hangi API 'Leri öğrenin.
ms.date: 12/23/2019
ms.openlocfilehash: f27aeca31226a95dacf100813762eedb56876fbd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936982"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="7553f-103">.NET Core üzerinde her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="7553f-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="7553f-104">Aşağıdaki API 'Ler her zaman bir platform alt kümesi üzerinde .NET Core üzerinde bir <xref:System.PlatformNotSupportedException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7553f-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="7553f-105">Bu makale, etkilenen API üyelerini ad alanına göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="7553f-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="7553f-106">Bu makale, devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="7553f-106">This article is a work-in-progress.</span></span> <span data-ttu-id="7553f-107">.NET Core üzerinde özel durum oluşturan API 'lerin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="7553f-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="7553f-108">Bu makale, .NET Core üzerinde throw ikili serileştirme için açık arabirim uygulamaları içermez.</span><span class="sxs-lookup"><span data-stu-id="7553f-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="7553f-109">Daha fazla bilgi için bkz. [.NET Core 'Da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="7553f-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="7553f-110">Sistem</span><span class="sxs-lookup"><span data-stu-id="7553f-110">System</span></span>

| <span data-ttu-id="7553f-111">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-111">Member</span></span> | <span data-ttu-id="7553f-112">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-113">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="7553f-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="7553f-115">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="7553f-116">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="7553f-118">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="7553f-119">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="7553f-120">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-121">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="7553f-122">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="7553f-123">System. CodeDom. derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7553f-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="7553f-124">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-124">Member</span></span> | <span data-ttu-id="7553f-125">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-127">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-128">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="7553f-129">System. Collections. özelleşmiş</span><span class="sxs-lookup"><span data-stu-id="7553f-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="7553f-130">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-130">Member</span></span> | <span data-ttu-id="7553f-131">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-132">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="7553f-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="7553f-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="7553f-135">System.Configuration</span></span>

| <span data-ttu-id="7553f-136">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-136">Member</span></span> | <span data-ttu-id="7553f-137">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="7553f-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="7553f-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="7553f-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="7553f-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="7553f-140">System.Console</span></span>

| <span data-ttu-id="7553f-141">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-141">Member</span></span> | <span data-ttu-id="7553f-142">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="7553f-143">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-143">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-145">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-145">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-147">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-147">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-149">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-149">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="7553f-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="7553f-151">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-152">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-153">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-154">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-154">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-155"><xref:System.Console.Title?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="7553f-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="7553f-156">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-156">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-158">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-158">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-160">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-160">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-162">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-162">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-164">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="7553f-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="7553f-165">System.Data.Common</span></span>

| <span data-ttu-id="7553f-166">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-166">Member</span></span> | <span data-ttu-id="7553f-167">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="7553f-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (<xref:System.NotSupportedException>oluşturur)</span><span class="sxs-lookup"><span data-stu-id="7553f-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="7553f-169">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="7553f-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="7553f-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="7553f-171">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-171">Member</span></span> | <span data-ttu-id="7553f-172">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="7553f-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-174">Linux</span><span class="sxs-lookup"><span data-stu-id="7553f-174">Linux</span></span> |
| <span data-ttu-id="7553f-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-176">Linux</span><span class="sxs-lookup"><span data-stu-id="7553f-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="7553f-177">macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="7553f-178">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-179">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="7553f-180">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="7553f-181">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="7553f-182">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="7553f-183">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-183">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-185">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-185">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="7553f-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="7553f-187">macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-187">macOS</span></span> |
| <span data-ttu-id="7553f-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-189">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="7553f-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="7553f-190">System.IO</span></span>

| <span data-ttu-id="7553f-191">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-191">Member</span></span> | <span data-ttu-id="7553f-192">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-193">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-194">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="7553f-195">System. ıO. Pipes</span><span class="sxs-lookup"><span data-stu-id="7553f-195">System.IO.Pipes</span></span>

| <span data-ttu-id="7553f-196">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-196">Member</span></span> | <span data-ttu-id="7553f-197">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="7553f-198">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="7553f-199">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="7553f-200">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="7553f-201">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-201">Linux and macOS</span></span> |
| <span data-ttu-id="7553f-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-203">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="7553f-204">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="7553f-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="7553f-205">System.Media</span></span>

| <span data-ttu-id="7553f-206">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-206">Member</span></span> | <span data-ttu-id="7553f-207">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-208">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="7553f-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="7553f-209">System.Net</span></span>

| <span data-ttu-id="7553f-210">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-210">Member</span></span> | <span data-ttu-id="7553f-211">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="7553f-212">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="7553f-213">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-214">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-215">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-216">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-217">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-218">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-219">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-220">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-221">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-222">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="7553f-223">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-224">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-225">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-226">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-227">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-228">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="7553f-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="7553f-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="7553f-230">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-230">Member</span></span> | <span data-ttu-id="7553f-231">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="7553f-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="7553f-233">System .net. Sockets</span><span class="sxs-lookup"><span data-stu-id="7553f-233">System.Net.Sockets</span></span>

| <span data-ttu-id="7553f-234">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-234">Member</span></span> | <span data-ttu-id="7553f-235">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="7553f-236">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-236">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="7553f-237">System .net. WebSockets</span><span class="sxs-lookup"><span data-stu-id="7553f-237">System.Net.WebSockets</span></span>

| <span data-ttu-id="7553f-238">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-238">Member</span></span> | <span data-ttu-id="7553f-239">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-239">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="7553f-240">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-240">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="7553f-241">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="7553f-241">System.Reflection</span></span>

| <span data-ttu-id="7553f-242">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-242">Member</span></span> | <span data-ttu-id="7553f-243">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-243">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-244">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-244">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7553f-245">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-245">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-246">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="7553f-247">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-247">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7553f-248">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-249">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="7553f-250">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-250">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="7553f-251">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="7553f-251">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="7553f-252">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-252">Member</span></span> | <span data-ttu-id="7553f-253">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-253">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="7553f-254">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-254">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="7553f-255">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="7553f-255">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="7553f-256">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-256">Member</span></span> | <span data-ttu-id="7553f-257">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-257">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="7553f-258">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-258">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="7553f-259">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="7553f-260">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="7553f-261">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-261">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7553f-262">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-262">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="7553f-263">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="7553f-264">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-264">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="7553f-265">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="7553f-265">System.Runtime.Serialization</span></span>

| <span data-ttu-id="7553f-266">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-266">Member</span></span> | <span data-ttu-id="7553f-267">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-267">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="7553f-268">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-268">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="7553f-269">System. Security</span><span class="sxs-lookup"><span data-stu-id="7553f-269">System.Security</span></span>

| <span data-ttu-id="7553f-270">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-270">Member</span></span> | <span data-ttu-id="7553f-271">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-271">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="7553f-272">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-272">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="7553f-273">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-273">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="7553f-274">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-274">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="7553f-275">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-275">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="7553f-276">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-276">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="7553f-277">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-277">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="7553f-278">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-278">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="7553f-279">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-279">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="7553f-280">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="7553f-281">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-281">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="7553f-282">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-282">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="7553f-283">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-283">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="7553f-284">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="7553f-285">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-285">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="7553f-286">System. Security. Claim</span><span class="sxs-lookup"><span data-stu-id="7553f-286">System.Security.Claims</span></span>

| <span data-ttu-id="7553f-287">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-287">Member</span></span> | <span data-ttu-id="7553f-288">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-288">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="7553f-289">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-289">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-290">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="7553f-291">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-292">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-293">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-293">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="7553f-294">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="7553f-294">System.Security.Cryptography</span></span>

| <span data-ttu-id="7553f-295">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-295">Member</span></span> | <span data-ttu-id="7553f-296">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-296">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7553f-297">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-297">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-298">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-298">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="7553f-299">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="7553f-300">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="7553f-301">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="7553f-302">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="7553f-303">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="7553f-304">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="7553f-305">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="7553f-306">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="7553f-307">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="7553f-308">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="7553f-309">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="7553f-310">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="7553f-311">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-311">All</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7553f-312">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="7553f-313">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7553f-314">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-315">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-316">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-317">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="7553f-318">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7553f-319">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-320">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-321">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7553f-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-322">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-323">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="7553f-324">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7553f-325">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="7553f-326">System. Security. Cryptography. Pkcs</span><span class="sxs-lookup"><span data-stu-id="7553f-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="7553f-327">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-327">Member</span></span> | <span data-ttu-id="7553f-328">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="7553f-329">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="7553f-330">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="7553f-331">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="7553f-332">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="7553f-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="7553f-333">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-333">Member</span></span> | <span data-ttu-id="7553f-334">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-335">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-336">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-337">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-337">All</span></span> |
| <span data-ttu-id="7553f-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7553f-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7553f-339">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="7553f-340">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="7553f-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="7553f-341">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-341">Member</span></span> | <span data-ttu-id="7553f-342">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-343">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="7553f-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="7553f-344">System.Security.Policy</span></span>

| <span data-ttu-id="7553f-345">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-345">Member</span></span> | <span data-ttu-id="7553f-346">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-347">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="7553f-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="7553f-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="7553f-349">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-349">Member</span></span> | <span data-ttu-id="7553f-350">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-351">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="7553f-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="7553f-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="7553f-353">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-353">Member</span></span> | <span data-ttu-id="7553f-354">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-355">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="7553f-356">System. Threading</span><span class="sxs-lookup"><span data-stu-id="7553f-356">System.Threading</span></span>

| <span data-ttu-id="7553f-357">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-357">Member</span></span> | <span data-ttu-id="7553f-358">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-359">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7553f-360">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="7553f-361">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="7553f-362">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="7553f-363">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="7553f-364">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="7553f-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="7553f-365">System.Xml</span></span>

| <span data-ttu-id="7553f-366">Üye</span><span class="sxs-lookup"><span data-stu-id="7553f-366">Member</span></span> | <span data-ttu-id="7553f-367">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7553f-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="7553f-368">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="7553f-369">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="7553f-370">Tümü</span><span class="sxs-lookup"><span data-stu-id="7553f-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="7553f-371">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7553f-371">See also</span></span>

- [<span data-ttu-id="7553f-372">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="7553f-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="7553f-373">.NET Core 'da ikili serileştirme</span><span class="sxs-lookup"><span data-stu-id="7553f-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="7553f-374">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="7553f-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
