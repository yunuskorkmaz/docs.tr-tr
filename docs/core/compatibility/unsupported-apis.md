---
title: .NET Core 'da desteklenmeyen API 'Ler
titleSuffix: ''
description: .NET Core üzerinde her zaman bir özel durum oluşturan .NET Framework hangi API 'Leri öğrenin.
ms.date: 12/23/2019
ms.openlocfilehash: c4b94321d30cacd90d5c2ee23c258681683a6faa
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092973"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="22f6a-103">.NET Core üzerinde her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="22f6a-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="22f6a-104">Aşağıdaki API 'Ler her zaman bir platform alt kümesi üzerinde .NET Core üzerinde bir <xref:System.PlatformNotSupportedException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22f6a-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="22f6a-105">Bu makale, etkilenen API üyelerini ad alanına göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="22f6a-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="22f6a-106">Bu makale, devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="22f6a-106">This article is a work-in-progress.</span></span> <span data-ttu-id="22f6a-107">.NET Core üzerinde özel durum oluşturan API 'lerin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="22f6a-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="22f6a-108">Bu makale, .NET Core üzerinde throw ikili serileştirme için açık arabirim uygulamaları içermez.</span><span class="sxs-lookup"><span data-stu-id="22f6a-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="22f6a-109">Daha fazla bilgi için bkz. [.NET Core 'Da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="22f6a-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="22f6a-110">Sistem</span><span class="sxs-lookup"><span data-stu-id="22f6a-110">System</span></span>

| <span data-ttu-id="22f6a-111">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-111">Member</span></span> | <span data-ttu-id="22f6a-112">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-113">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="22f6a-115">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="22f6a-116">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="22f6a-118">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="22f6a-119">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="22f6a-120">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-121">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-122">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="22f6a-123">System. CodeDom. derleyicisi</span><span class="sxs-lookup"><span data-stu-id="22f6a-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="22f6a-124">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-124">Member</span></span> | <span data-ttu-id="22f6a-125">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-127">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-128">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="22f6a-129">System. Collections. özelleşmiş</span><span class="sxs-lookup"><span data-stu-id="22f6a-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="22f6a-130">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-130">Member</span></span> | <span data-ttu-id="22f6a-131">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-132">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="22f6a-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="22f6a-135">System.Configuration</span></span>

| <span data-ttu-id="22f6a-136">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-136">Member</span></span> | <span data-ttu-id="22f6a-137">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="22f6a-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="22f6a-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="22f6a-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="22f6a-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="22f6a-140">System.Console</span></span>

| <span data-ttu-id="22f6a-141">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-141">Member</span></span> | <span data-ttu-id="22f6a-142">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="22f6a-143">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-143">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-145">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-145">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-147">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-147">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-149">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-149">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="22f6a-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="22f6a-151">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-152">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-153">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-154">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-154">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-155"><xref:System.Console.Title?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="22f6a-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="22f6a-156">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-156">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-158">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-158">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-160">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-160">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-162">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-162">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-164">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="22f6a-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="22f6a-165">System.Data.Common</span></span>

| <span data-ttu-id="22f6a-166">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-166">Member</span></span> | <span data-ttu-id="22f6a-167">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="22f6a-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (<xref:System.NotSupportedException>oluşturur)</span><span class="sxs-lookup"><span data-stu-id="22f6a-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="22f6a-169">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="22f6a-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="22f6a-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="22f6a-171">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-171">Member</span></span> | <span data-ttu-id="22f6a-172">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="22f6a-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-174">Linux</span><span class="sxs-lookup"><span data-stu-id="22f6a-174">Linux</span></span> |
| <span data-ttu-id="22f6a-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-176">Linux</span><span class="sxs-lookup"><span data-stu-id="22f6a-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="22f6a-177">Mac OS</span><span class="sxs-lookup"><span data-stu-id="22f6a-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="22f6a-178">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-179">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="22f6a-180">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="22f6a-181">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="22f6a-182">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="22f6a-183">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-183">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-185">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-185">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="22f6a-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="22f6a-187">Mac OS</span><span class="sxs-lookup"><span data-stu-id="22f6a-187">macOS</span></span> |
| <span data-ttu-id="22f6a-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-189">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="22f6a-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="22f6a-190">System.IO</span></span>

| <span data-ttu-id="22f6a-191">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-191">Member</span></span> | <span data-ttu-id="22f6a-192">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-193">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-194">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="22f6a-195">System. ıO. Pipes</span><span class="sxs-lookup"><span data-stu-id="22f6a-195">System.IO.Pipes</span></span>

| <span data-ttu-id="22f6a-196">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-196">Member</span></span> | <span data-ttu-id="22f6a-197">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="22f6a-198">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="22f6a-199">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="22f6a-200">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="22f6a-201">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-201">Linux and macOS</span></span> |
| <span data-ttu-id="22f6a-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-203">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="22f6a-204">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="22f6a-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="22f6a-205">System.Media</span></span>

| <span data-ttu-id="22f6a-206">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-206">Member</span></span> | <span data-ttu-id="22f6a-207">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-208">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="22f6a-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="22f6a-209">System.Net</span></span>

| <span data-ttu-id="22f6a-210">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-210">Member</span></span> | <span data-ttu-id="22f6a-211">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-212">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-213">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-214">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-215">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-216">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-217">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-218">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-219">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-220">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-221">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-222">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="22f6a-223">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-224">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-225">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-226">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-227">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-228">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="22f6a-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="22f6a-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="22f6a-230">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-230">Member</span></span> | <span data-ttu-id="22f6a-231">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="22f6a-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="22f6a-233">System .net. Sockets</span><span class="sxs-lookup"><span data-stu-id="22f6a-233">System.Net.Sockets</span></span>

| <span data-ttu-id="22f6a-234">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-234">Member</span></span> | <span data-ttu-id="22f6a-235">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-236">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-237">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="22f6a-238">System .net. WebSockets</span><span class="sxs-lookup"><span data-stu-id="22f6a-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="22f6a-239">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-239">Member</span></span> | <span data-ttu-id="22f6a-240">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="22f6a-241">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="22f6a-242">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="22f6a-242">System.Reflection</span></span>

| <span data-ttu-id="22f6a-243">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-243">Member</span></span> | <span data-ttu-id="22f6a-244">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-245">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-246">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-247">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-248">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-249">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-250">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="22f6a-251">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="22f6a-252">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="22f6a-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="22f6a-253">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-253">Member</span></span> | <span data-ttu-id="22f6a-254">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="22f6a-255">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="22f6a-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="22f6a-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="22f6a-257">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-257">Member</span></span> | <span data-ttu-id="22f6a-258">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-259">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="22f6a-260">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-261">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-262">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-263">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-264">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-265">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="22f6a-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="22f6a-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="22f6a-267">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-267">Member</span></span> | <span data-ttu-id="22f6a-268">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="22f6a-269">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="22f6a-270">System. Security</span><span class="sxs-lookup"><span data-stu-id="22f6a-270">System.Security</span></span>

| <span data-ttu-id="22f6a-271">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-271">Member</span></span> | <span data-ttu-id="22f6a-272">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="22f6a-273">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="22f6a-274">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-275">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="22f6a-276">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="22f6a-277">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="22f6a-278">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="22f6a-279">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="22f6a-280">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="22f6a-281">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="22f6a-282">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="22f6a-283">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-284">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="22f6a-285">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="22f6a-286">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="22f6a-287">System. Security. Claim</span><span class="sxs-lookup"><span data-stu-id="22f6a-287">System.Security.Claims</span></span>

| <span data-ttu-id="22f6a-288">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-288">Member</span></span> | <span data-ttu-id="22f6a-289">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="22f6a-290">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-291">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-292">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-293">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-294">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="22f6a-295">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="22f6a-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="22f6a-296">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-296">Member</span></span> | <span data-ttu-id="22f6a-297">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-298">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-299">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="22f6a-300">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="22f6a-301">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="22f6a-302">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="22f6a-303">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="22f6a-304">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="22f6a-305">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="22f6a-306">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="22f6a-307">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="22f6a-308">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="22f6a-309">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="22f6a-310">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="22f6a-311">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="22f6a-312">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="22f6a-313">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-314">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-315">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-316">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-317">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="22f6a-318">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-319">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-320">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-321">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="22f6a-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-322">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-323">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="22f6a-324">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-325">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="22f6a-326">System. Security. Cryptography. Pkcs</span><span class="sxs-lookup"><span data-stu-id="22f6a-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="22f6a-327">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-327">Member</span></span> | <span data-ttu-id="22f6a-328">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-329">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-330">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="22f6a-331">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="22f6a-332">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="22f6a-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="22f6a-333">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-333">Member</span></span> | <span data-ttu-id="22f6a-334">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-335">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-336">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-337">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-337">All</span></span> |
| <span data-ttu-id="22f6a-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="22f6a-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22f6a-339">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="22f6a-340">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="22f6a-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="22f6a-341">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-341">Member</span></span> | <span data-ttu-id="22f6a-342">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-343">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="22f6a-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="22f6a-344">System.Security.Policy</span></span>

| <span data-ttu-id="22f6a-345">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-345">Member</span></span> | <span data-ttu-id="22f6a-346">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-347">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="22f6a-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="22f6a-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="22f6a-349">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-349">Member</span></span> | <span data-ttu-id="22f6a-350">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-351">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="22f6a-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="22f6a-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="22f6a-353">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-353">Member</span></span> | <span data-ttu-id="22f6a-354">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-355">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="22f6a-356">System. Threading</span><span class="sxs-lookup"><span data-stu-id="22f6a-356">System.Threading</span></span>

| <span data-ttu-id="22f6a-357">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-357">Member</span></span> | <span data-ttu-id="22f6a-358">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-359">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-360">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="22f6a-361">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="22f6a-362">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="22f6a-363">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="22f6a-364">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="22f6a-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="22f6a-365">System.Xml</span></span>

| <span data-ttu-id="22f6a-366">Üyesi</span><span class="sxs-lookup"><span data-stu-id="22f6a-366">Member</span></span> | <span data-ttu-id="22f6a-367">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="22f6a-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-368">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-369">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="22f6a-370">Tümü</span><span class="sxs-lookup"><span data-stu-id="22f6a-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="22f6a-371">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22f6a-371">See also</span></span>

- [<span data-ttu-id="22f6a-372">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="22f6a-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="22f6a-373">.NET Core 'da ikili serileştirme</span><span class="sxs-lookup"><span data-stu-id="22f6a-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="22f6a-374">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="22f6a-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
