---
title: .NET Core 'da desteklenmeyen API 'Ler
titleSuffix: ''
description: .NET Core üzerinde her zaman bir özel durum oluşturan .NET Framework hangi API 'Leri öğrenin.
ms.date: 12/23/2019
ms.openlocfilehash: 94f334d7e4b7daf407f489ba274172ced9eefa81
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414441"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="71cab-103">.NET Core üzerinde her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="71cab-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="71cab-104">Aşağıdaki API 'Ler her zaman bir <xref:System.PlatformNotSupportedException> Platform alt kümesi üzerinde .NET Core üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="71cab-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="71cab-105">Bu makale, etkilenen API üyelerini ad alanına göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="71cab-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="71cab-106">Bu makale, devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="71cab-106">This article is a work-in-progress.</span></span> <span data-ttu-id="71cab-107">.NET Core üzerinde özel durum oluşturan API 'lerin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="71cab-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="71cab-108">Bu makale, .NET Core üzerinde throw ikili serileştirme için açık arabirim uygulamaları içermez.</span><span class="sxs-lookup"><span data-stu-id="71cab-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="71cab-109">Daha fazla bilgi için bkz. [.NET Core 'Da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="71cab-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="71cab-110">Sistem</span><span class="sxs-lookup"><span data-stu-id="71cab-110">System</span></span>

| <span data-ttu-id="71cab-111">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-111">Member</span></span> | <span data-ttu-id="71cab-112">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-113">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="71cab-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="71cab-115">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="71cab-116">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="71cab-118">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="71cab-119">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="71cab-120">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-121">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="71cab-122">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="71cab-123">System. CodeDom. derleyicisi</span><span class="sxs-lookup"><span data-stu-id="71cab-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="71cab-124">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-124">Member</span></span> | <span data-ttu-id="71cab-125">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-127">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-128">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="71cab-129">System. Collections. özelleşmiş</span><span class="sxs-lookup"><span data-stu-id="71cab-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="71cab-130">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-130">Member</span></span> | <span data-ttu-id="71cab-131">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-132">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="71cab-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="71cab-135">System.Configurlama</span><span class="sxs-lookup"><span data-stu-id="71cab-135">System.Configuration</span></span>

| <span data-ttu-id="71cab-136">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-136">Member</span></span> | <span data-ttu-id="71cab-137">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="71cab-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="71cab-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="71cab-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="71cab-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="71cab-140">System.Console</span></span>

| <span data-ttu-id="71cab-141">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-141">Member</span></span> | <span data-ttu-id="71cab-142">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="71cab-143">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-143">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-145">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-145">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-147">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-147">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-149">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-149">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="71cab-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="71cab-151">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-152">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-153">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-154">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-154">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-155"><xref:System.Console.Title?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="71cab-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="71cab-156">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-156">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-158">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-158">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-160">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-160">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-162">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-162">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-164">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="71cab-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="71cab-165">System.Data.Common</span></span>

| <span data-ttu-id="71cab-166">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-166">Member</span></span> | <span data-ttu-id="71cab-167">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="71cab-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (atar <xref:System.NotSupportedException> )</span><span class="sxs-lookup"><span data-stu-id="71cab-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="71cab-169">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="71cab-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="71cab-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="71cab-171">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-171">Member</span></span> | <span data-ttu-id="71cab-172">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="71cab-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-174">Linux</span><span class="sxs-lookup"><span data-stu-id="71cab-174">Linux</span></span> |
| <span data-ttu-id="71cab-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-176">Linux</span><span class="sxs-lookup"><span data-stu-id="71cab-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="71cab-177">macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="71cab-178">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-179">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="71cab-180">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="71cab-181">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="71cab-182">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="71cab-183">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-183">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-185">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-185">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="71cab-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="71cab-187">macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-187">macOS</span></span> |
| <span data-ttu-id="71cab-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-189">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="71cab-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="71cab-190">System.IO</span></span>

| <span data-ttu-id="71cab-191">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-191">Member</span></span> | <span data-ttu-id="71cab-192">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-193">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-194">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="71cab-195">System. ıO. Pipes</span><span class="sxs-lookup"><span data-stu-id="71cab-195">System.IO.Pipes</span></span>

| <span data-ttu-id="71cab-196">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-196">Member</span></span> | <span data-ttu-id="71cab-197">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="71cab-198">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="71cab-199">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="71cab-200">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="71cab-201">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-201">Linux and macOS</span></span> |
| <span data-ttu-id="71cab-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-203">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="71cab-204">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="71cab-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="71cab-205">System.Media</span></span>

| <span data-ttu-id="71cab-206">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-206">Member</span></span> | <span data-ttu-id="71cab-207">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-208">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="71cab-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="71cab-209">System.Net</span></span>

| <span data-ttu-id="71cab-210">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-210">Member</span></span> | <span data-ttu-id="71cab-211">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="71cab-212">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="71cab-213">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-214">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-215">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-216">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-217">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-218">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-219">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-220">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-221">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-222">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="71cab-223">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-224">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-225">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-226">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-227">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-228">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="71cab-229">System .net. NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="71cab-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="71cab-230">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-230">Member</span></span> | <span data-ttu-id="71cab-231">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="71cab-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="71cab-233">System .net. Sockets</span><span class="sxs-lookup"><span data-stu-id="71cab-233">System.Net.Sockets</span></span>

| <span data-ttu-id="71cab-234">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-234">Member</span></span> | <span data-ttu-id="71cab-235">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="71cab-236">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="71cab-237">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="71cab-238">System .net. WebSockets</span><span class="sxs-lookup"><span data-stu-id="71cab-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="71cab-239">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-239">Member</span></span> | <span data-ttu-id="71cab-240">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="71cab-241">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="71cab-242">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="71cab-242">System.Reflection</span></span>

| <span data-ttu-id="71cab-243">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-243">Member</span></span> | <span data-ttu-id="71cab-244">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-245">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="71cab-246">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-247">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="71cab-248">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="71cab-249">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-250">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="71cab-251">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="71cab-252">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="71cab-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="71cab-253">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-253">Member</span></span> | <span data-ttu-id="71cab-254">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="71cab-255">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="71cab-256">System. Runtime. InteropServices</span><span class="sxs-lookup"><span data-stu-id="71cab-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="71cab-257">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-257">Member</span></span> | <span data-ttu-id="71cab-258">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="71cab-259">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="71cab-260">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="71cab-261">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="71cab-262">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="71cab-263">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="71cab-264">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="71cab-265">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="71cab-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="71cab-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="71cab-267">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-267">Member</span></span> | <span data-ttu-id="71cab-268">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="71cab-269">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="71cab-270">System. Security</span><span class="sxs-lookup"><span data-stu-id="71cab-270">System.Security</span></span>

| <span data-ttu-id="71cab-271">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-271">Member</span></span> | <span data-ttu-id="71cab-272">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="71cab-273">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="71cab-274">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="71cab-275">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="71cab-276">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="71cab-277">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="71cab-278">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="71cab-279">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="71cab-280">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="71cab-281">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="71cab-282">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="71cab-283">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="71cab-284">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="71cab-285">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="71cab-286">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="71cab-287">System. Security. Claim</span><span class="sxs-lookup"><span data-stu-id="71cab-287">System.Security.Claims</span></span>

| <span data-ttu-id="71cab-288">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-288">Member</span></span> | <span data-ttu-id="71cab-289">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="71cab-290">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-291">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="71cab-292">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-293">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-294">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="71cab-295">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="71cab-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="71cab-296">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-296">Member</span></span> | <span data-ttu-id="71cab-297">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="71cab-298">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="71cab-299">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="71cab-300">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="71cab-301">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="71cab-302">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="71cab-303">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="71cab-304">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="71cab-305">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="71cab-306">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="71cab-307">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="71cab-308">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="71cab-309">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="71cab-310">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="71cab-311">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="71cab-312">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="71cab-313">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="71cab-314">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-315">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-316">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-317">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="71cab-318">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="71cab-319">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-320">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-321">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="71cab-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-322">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-323">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="71cab-324">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="71cab-325">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="71cab-326">System. Security. Cryptography. Pkcs</span><span class="sxs-lookup"><span data-stu-id="71cab-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="71cab-327">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-327">Member</span></span> | <span data-ttu-id="71cab-328">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="71cab-329">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="71cab-330">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="71cab-331">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="71cab-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="71cab-332">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-332">Member</span></span> | <span data-ttu-id="71cab-333">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-334">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-335">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-336">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-336">All</span></span> |
| <span data-ttu-id="71cab-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="71cab-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="71cab-338">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="71cab-339">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="71cab-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="71cab-340">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-340">Member</span></span> | <span data-ttu-id="71cab-341">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-342">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="71cab-343">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="71cab-343">System.Security.Policy</span></span>

| <span data-ttu-id="71cab-344">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-344">Member</span></span> | <span data-ttu-id="71cab-345">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-346">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="71cab-347">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="71cab-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="71cab-348">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-348">Member</span></span> | <span data-ttu-id="71cab-349">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="71cab-350">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="71cab-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="71cab-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="71cab-352">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-352">Member</span></span> | <span data-ttu-id="71cab-353">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-354">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="71cab-355">System. Threading</span><span class="sxs-lookup"><span data-stu-id="71cab-355">System.Threading</span></span>

| <span data-ttu-id="71cab-356">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-356">Member</span></span> | <span data-ttu-id="71cab-357">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-358">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="71cab-359">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="71cab-360">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="71cab-361">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="71cab-362">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="71cab-363">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="71cab-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="71cab-364">System.Xml</span></span>

| <span data-ttu-id="71cab-365">Üye</span><span class="sxs-lookup"><span data-stu-id="71cab-365">Member</span></span> | <span data-ttu-id="71cab-366">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="71cab-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="71cab-367">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="71cab-368">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="71cab-369">Tümü</span><span class="sxs-lookup"><span data-stu-id="71cab-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="71cab-370">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71cab-370">See also</span></span>

- [<span data-ttu-id="71cab-371">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="71cab-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="71cab-372">.NET Core 'da ikili serileştirme</span><span class="sxs-lookup"><span data-stu-id="71cab-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="71cab-373">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="71cab-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
