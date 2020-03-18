---
title: .NET Core'da Desteklenmeyen API'ler
titleSuffix: ''
description: .NET Core'da her zaman özel durum oluşturan .NET Framework'den hangi API'lerin olduğunu öğrenin.
ms.date: 12/23/2019
ms.openlocfilehash: c4b94321d30cacd90d5c2ee23c258681683a6faa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092973"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="c50fb-103">.NET Core'da her zaman özel durumlar oluşturan API'ler</span><span class="sxs-lookup"><span data-stu-id="c50fb-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="c50fb-104">Aşağıdaki API'ler her <xref:System.PlatformNotSupportedException> zaman .NET Core'un tümüne veya bir platform alt kümesine bir</span><span class="sxs-lookup"><span data-stu-id="c50fb-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="c50fb-105">Bu makalede, etkilenen API üyeleri ad alanına göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="c50fb-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="c50fb-106">Bu makale, devam etmekte olan bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="c50fb-106">This article is a work-in-progress.</span></span> <span data-ttu-id="c50fb-107">.NET Core'da özel durumlar oluşturan API'lerin tam bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="c50fb-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="c50fb-108">Bu makalede, .NET Core'u oluşturan ikili serileştirme için açık arabirim uygulamaları içermez.</span><span class="sxs-lookup"><span data-stu-id="c50fb-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="c50fb-109">Daha fazla bilgi için [.NET Core'daki İkili serileştirmeye](../../standard/serialization/binary-serialization.md#net-core)bakın.</span><span class="sxs-lookup"><span data-stu-id="c50fb-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="c50fb-110">Sistem</span><span class="sxs-lookup"><span data-stu-id="c50fb-110">System</span></span>

| <span data-ttu-id="c50fb-111">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-111">Member</span></span> | <span data-ttu-id="c50fb-112">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-113">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="c50fb-115">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="c50fb-116">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="c50fb-118">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="c50fb-119">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="c50fb-120">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-121">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-122">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="c50fb-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="c50fb-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="c50fb-124">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-124">Member</span></span> | <span data-ttu-id="c50fb-125">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-127">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-128">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="c50fb-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="c50fb-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="c50fb-130">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-130">Member</span></span> | <span data-ttu-id="c50fb-131">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-132">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="c50fb-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="c50fb-135">System.Configuration</span></span>

| <span data-ttu-id="c50fb-136">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-136">Member</span></span> | <span data-ttu-id="c50fb-137">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="c50fb-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="c50fb-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="c50fb-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="c50fb-140">Console</span><span class="sxs-lookup"><span data-stu-id="c50fb-140">System.Console</span></span>

| <span data-ttu-id="c50fb-141">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-141">Member</span></span> | <span data-ttu-id="c50fb-142">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="c50fb-143">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-143">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-145">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-145">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-147">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-147">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-149">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-149">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(yalnızca almak)</span><span class="sxs-lookup"><span data-stu-id="c50fb-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="c50fb-151">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-152">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-153">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-154">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-154">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-155"><xref:System.Console.Title?displayProperty=nameWithType>(yalnızca almak)</span><span class="sxs-lookup"><span data-stu-id="c50fb-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="c50fb-156">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-156">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-158">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-158">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-160">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-160">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-162">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-162">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-164">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="c50fb-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="c50fb-165">System.Data.Common</span></span>

| <span data-ttu-id="c50fb-166">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-166">Member</span></span> | <span data-ttu-id="c50fb-167">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="c50fb-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(atar <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="c50fb-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="c50fb-169">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="c50fb-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="c50fb-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="c50fb-171">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-171">Member</span></span> | <span data-ttu-id="c50fb-172">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="c50fb-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-174">Linux</span><span class="sxs-lookup"><span data-stu-id="c50fb-174">Linux</span></span> |
| <span data-ttu-id="c50fb-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-176">Linux</span><span class="sxs-lookup"><span data-stu-id="c50fb-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="c50fb-177">macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="c50fb-178">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-179">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="c50fb-180">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="c50fb-181">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="c50fb-182">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="c50fb-183">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-183">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-185">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-185">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(yalnızca almak)</span><span class="sxs-lookup"><span data-stu-id="c50fb-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="c50fb-187">macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-187">macOS</span></span> |
| <span data-ttu-id="c50fb-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-189">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="c50fb-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="c50fb-190">System.IO</span></span>

| <span data-ttu-id="c50fb-191">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-191">Member</span></span> | <span data-ttu-id="c50fb-192">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-193">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-194">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="c50fb-195">Pipes</span><span class="sxs-lookup"><span data-stu-id="c50fb-195">System.IO.Pipes</span></span>

| <span data-ttu-id="c50fb-196">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-196">Member</span></span> | <span data-ttu-id="c50fb-197">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="c50fb-198">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="c50fb-199">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="c50fb-200">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="c50fb-201">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-201">Linux and macOS</span></span> |
| <span data-ttu-id="c50fb-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-203">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="c50fb-204">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="c50fb-205">Media</span><span class="sxs-lookup"><span data-stu-id="c50fb-205">System.Media</span></span>

| <span data-ttu-id="c50fb-206">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-206">Member</span></span> | <span data-ttu-id="c50fb-207">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-208">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="c50fb-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="c50fb-209">System.Net</span></span>

| <span data-ttu-id="c50fb-210">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-210">Member</span></span> | <span data-ttu-id="c50fb-211">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-212">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-213">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-214">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-215">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-216">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-217">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-218">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-219">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-220">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-221">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-222">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="c50fb-223">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-224">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-225">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-226">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-227">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-228">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="c50fb-229">Networkınformation</span><span class="sxs-lookup"><span data-stu-id="c50fb-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="c50fb-230">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-230">Member</span></span> | <span data-ttu-id="c50fb-231">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="c50fb-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="c50fb-233">Sockets</span><span class="sxs-lookup"><span data-stu-id="c50fb-233">System.Net.Sockets</span></span>

| <span data-ttu-id="c50fb-234">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-234">Member</span></span> | <span data-ttu-id="c50fb-235">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-236">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-237">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="c50fb-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="c50fb-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="c50fb-239">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-239">Member</span></span> | <span data-ttu-id="c50fb-240">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="c50fb-241">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="c50fb-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="c50fb-242">System.Reflection</span></span>

| <span data-ttu-id="c50fb-243">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-243">Member</span></span> | <span data-ttu-id="c50fb-244">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-245">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-246">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-247">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-248">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-249">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-250">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="c50fb-251">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="c50fb-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="c50fb-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="c50fb-253">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-253">Member</span></span> | <span data-ttu-id="c50fb-254">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="c50fb-255">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="c50fb-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="c50fb-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="c50fb-257">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-257">Member</span></span> | <span data-ttu-id="c50fb-258">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-259">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="c50fb-260">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-261">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-262">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-263">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-264">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-265">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="c50fb-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="c50fb-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="c50fb-267">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-267">Member</span></span> | <span data-ttu-id="c50fb-268">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="c50fb-269">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="c50fb-270">Security</span><span class="sxs-lookup"><span data-stu-id="c50fb-270">System.Security</span></span>

| <span data-ttu-id="c50fb-271">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-271">Member</span></span> | <span data-ttu-id="c50fb-272">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="c50fb-273">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="c50fb-274">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-275">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="c50fb-276">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="c50fb-277">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="c50fb-278">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="c50fb-279">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="c50fb-280">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="c50fb-281">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="c50fb-282">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="c50fb-283">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-284">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="c50fb-285">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="c50fb-286">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="c50fb-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="c50fb-287">System.Security.Claims</span></span>

| <span data-ttu-id="c50fb-288">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-288">Member</span></span> | <span data-ttu-id="c50fb-289">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="c50fb-290">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-291">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-292">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-293">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-294">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="c50fb-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="c50fb-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="c50fb-296">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-296">Member</span></span> | <span data-ttu-id="c50fb-297">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-298">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-299">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="c50fb-300">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="c50fb-301">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="c50fb-302">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="c50fb-303">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="c50fb-304">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="c50fb-305">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="c50fb-306">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="c50fb-307">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="c50fb-308">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="c50fb-309">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="c50fb-310">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="c50fb-311">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="c50fb-312">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="c50fb-313">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-314">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-315">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-316">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-317">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="c50fb-318">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-319">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-320">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-321">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="c50fb-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-322">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-323">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="c50fb-324">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-325">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="c50fb-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="c50fb-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="c50fb-327">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-327">Member</span></span> | <span data-ttu-id="c50fb-328">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-329">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-330">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="c50fb-331">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="c50fb-332">System.Security.Cryptography.X509Sertifikalar</span><span class="sxs-lookup"><span data-stu-id="c50fb-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="c50fb-333">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-333">Member</span></span> | <span data-ttu-id="c50fb-334">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-335">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-336">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-337">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-337">All</span></span> |
| <span data-ttu-id="c50fb-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(yalnızca ayar)</span><span class="sxs-lookup"><span data-stu-id="c50fb-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="c50fb-339">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="c50fb-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="c50fb-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="c50fb-341">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-341">Member</span></span> | <span data-ttu-id="c50fb-342">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-343">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="c50fb-344">System.Security.Policy</span><span class="sxs-lookup"><span data-stu-id="c50fb-344">System.Security.Policy</span></span>

| <span data-ttu-id="c50fb-345">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-345">Member</span></span> | <span data-ttu-id="c50fb-346">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-347">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="c50fb-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="c50fb-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="c50fb-349">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-349">Member</span></span> | <span data-ttu-id="c50fb-350">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-351">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="c50fb-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="c50fb-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="c50fb-353">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-353">Member</span></span> | <span data-ttu-id="c50fb-354">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-355">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="c50fb-356">Threading</span><span class="sxs-lookup"><span data-stu-id="c50fb-356">System.Threading</span></span>

| <span data-ttu-id="c50fb-357">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-357">Member</span></span> | <span data-ttu-id="c50fb-358">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-359">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-360">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="c50fb-361">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="c50fb-362">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="c50fb-363">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="c50fb-364">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="c50fb-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="c50fb-365">System.Xml</span></span>

| <span data-ttu-id="c50fb-366">Üye</span><span class="sxs-lookup"><span data-stu-id="c50fb-366">Member</span></span> | <span data-ttu-id="c50fb-367">Atan platformlar</span><span class="sxs-lookup"><span data-stu-id="c50fb-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-368">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-369">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="c50fb-370">Tümü</span><span class="sxs-lookup"><span data-stu-id="c50fb-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="c50fb-371">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c50fb-371">See also</span></span>

- [<span data-ttu-id="c50fb-372">.NET Framework'den .NET Core'a geçiş için son dakika değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="c50fb-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="c50fb-373">.NET Core'da ikili serileştirme</span><span class="sxs-lookup"><span data-stu-id="c50fb-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="c50fb-374">.NET taşınabilirlik analizörü</span><span class="sxs-lookup"><span data-stu-id="c50fb-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
