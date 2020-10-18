---
title: .NET Core ve .NET 5 + üzerinde desteklenmeyen API 'Ler
titleSuffix: ''
description: .NET API 'Lerin hangi .NET Core ve .NET 5,0 ve sonraki sürümlerinde her zaman bir istisna sağladığını öğrenin.
ms.date: 10/13/2020
ms.openlocfilehash: 0164ebff51de82d548a02f9fde754c1052a9c2b5
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159345"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="f5d0c-103">.NET Core ve .NET 5 + ' da her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="f5d0c-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="f5d0c-104">Aşağıdaki API 'Ler her zaman bir <xref:System.PlatformNotSupportedException> Platform alt kümesi üzerinde .net 5,0 ve sonraki sürümlerinde (.NET Core 'un tüm sürümleri dahil) her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f5d0c-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="f5d0c-105">Bu makale, etkilenen API 'Leri ad alanına göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="f5d0c-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="f5d0c-106">Bu makale, devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="f5d0c-106">This article is a work-in-progress.</span></span> <span data-ttu-id="f5d0c-107">.NET 5 + ' da özel durum oluşturan API 'lerin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="f5d0c-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="f5d0c-108">Bu makalede, .NET 5 + ' de oluşturan ikili serileştirme için açık arabirim uygulamaları dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="f5d0c-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="f5d0c-109">Daha fazla bilgi için bkz. [.NET Core 'Da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="f5d0c-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="f5d0c-110">Sistem</span><span class="sxs-lookup"><span data-stu-id="f5d0c-110">System</span></span>

| <span data-ttu-id="f5d0c-111">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-111">Member</span></span> | <span data-ttu-id="f5d0c-112">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-113">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-115">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-116">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-118">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-119">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-120">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-121">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-122">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="f5d0c-123">System. CodeDom. derleyicisi</span><span class="sxs-lookup"><span data-stu-id="f5d0c-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="f5d0c-124">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-124">Member</span></span> | <span data-ttu-id="f5d0c-125">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-127">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-128">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="f5d0c-129">System. Collections. özelleşmiş</span><span class="sxs-lookup"><span data-stu-id="f5d0c-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="f5d0c-130">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-130">Member</span></span> | <span data-ttu-id="f5d0c-131">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-132">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="f5d0c-135">System.Configurlama</span><span class="sxs-lookup"><span data-stu-id="f5d0c-135">System.Configuration</span></span>

| <span data-ttu-id="f5d0c-136">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-136">Member</span></span> | <span data-ttu-id="f5d0c-137">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="f5d0c-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="f5d0c-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="f5d0c-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="f5d0c-140">System.Console</span></span>

| <span data-ttu-id="f5d0c-141">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-141">Member</span></span> | <span data-ttu-id="f5d0c-142">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-143">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-143">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-145">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-145">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-147">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-147">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-149">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-149">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="f5d0c-151">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-152">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-153">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-154">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-154">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-155"><xref:System.Console.Title?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="f5d0c-156">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-156">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-158">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-158">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-160">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-160">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-162">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-162">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-164">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="f5d0c-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="f5d0c-165">System.Data.Common</span></span>

| <span data-ttu-id="f5d0c-166">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-166">Member</span></span> | <span data-ttu-id="f5d0c-167">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="f5d0c-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (atar <xref:System.NotSupportedException> )</span><span class="sxs-lookup"><span data-stu-id="f5d0c-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="f5d0c-169">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="f5d0c-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="f5d0c-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="f5d0c-171">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-171">Member</span></span> | <span data-ttu-id="f5d0c-172">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="f5d0c-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-174">Linux</span><span class="sxs-lookup"><span data-stu-id="f5d0c-174">Linux</span></span> |
| <span data-ttu-id="f5d0c-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-176">Linux</span><span class="sxs-lookup"><span data-stu-id="f5d0c-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-177">macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-178">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-179">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-180">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-181">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-182">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-183">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-183">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-185">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-185">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="f5d0c-187">macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-187">macOS</span></span> |
| <span data-ttu-id="f5d0c-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-189">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="f5d0c-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="f5d0c-190">System.IO</span></span>

| <span data-ttu-id="f5d0c-191">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-191">Member</span></span> | <span data-ttu-id="f5d0c-192">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-193">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-194">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="f5d0c-195">System. ıO. Pipes</span><span class="sxs-lookup"><span data-stu-id="f5d0c-195">System.IO.Pipes</span></span>

| <span data-ttu-id="f5d0c-196">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-196">Member</span></span> | <span data-ttu-id="f5d0c-197">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-198">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-199">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-200">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-201">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-201">Linux and macOS</span></span> |
| <span data-ttu-id="f5d0c-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-203">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-204">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="f5d0c-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="f5d0c-205">System.Media</span></span>

| <span data-ttu-id="f5d0c-206">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-206">Member</span></span> | <span data-ttu-id="f5d0c-207">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-208">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="f5d0c-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="f5d0c-209">System.Net</span></span>

| <span data-ttu-id="f5d0c-210">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-210">Member</span></span> | <span data-ttu-id="f5d0c-211">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-212">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-213">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-214">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-215">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-216">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-217">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-218">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-219">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-220">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-221">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-222">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-223">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-224">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-225">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-226">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-227">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-228">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="f5d0c-229">System .net. NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="f5d0c-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="f5d0c-230">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-230">Member</span></span> | <span data-ttu-id="f5d0c-231">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="f5d0c-233">System .net. Sockets</span><span class="sxs-lookup"><span data-stu-id="f5d0c-233">System.Net.Sockets</span></span>

| <span data-ttu-id="f5d0c-234">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-234">Member</span></span> | <span data-ttu-id="f5d0c-235">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="f5d0c-236">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-237">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="f5d0c-238">System .net. WebSockets</span><span class="sxs-lookup"><span data-stu-id="f5d0c-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="f5d0c-239">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-239">Member</span></span> | <span data-ttu-id="f5d0c-240">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-241">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="f5d0c-242">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="f5d0c-242">System.Reflection</span></span>

| <span data-ttu-id="f5d0c-243">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-243">Member</span></span> | <span data-ttu-id="f5d0c-244">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-245">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-246">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-247">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-248">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="f5d0c-249">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-250">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-251">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="f5d0c-252">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="f5d0c-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="f5d0c-253">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-253">Member</span></span> | <span data-ttu-id="f5d0c-254">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-255">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="f5d0c-256">System. Runtime. InteropServices</span><span class="sxs-lookup"><span data-stu-id="f5d0c-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="f5d0c-257">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-257">Member</span></span> | <span data-ttu-id="f5d0c-258">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-259">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-260">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-261">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-262">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-263">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-264">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-265">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="f5d0c-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="f5d0c-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="f5d0c-267">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-267">Member</span></span> | <span data-ttu-id="f5d0c-268">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-269">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="f5d0c-270">System. Security</span><span class="sxs-lookup"><span data-stu-id="f5d0c-270">System.Security</span></span>

| <span data-ttu-id="f5d0c-271">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-271">Member</span></span> | <span data-ttu-id="f5d0c-272">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-273">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-274">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-275">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-276">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-277">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-278">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-279">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-280">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-281">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-282">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-283">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-284">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-285">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-286">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="f5d0c-287">System. Security. Claim</span><span class="sxs-lookup"><span data-stu-id="f5d0c-287">System.Security.Claims</span></span>

| <span data-ttu-id="f5d0c-288">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-288">Member</span></span> | <span data-ttu-id="f5d0c-289">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="f5d0c-290">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-291">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="f5d0c-292">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-293">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-294">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="f5d0c-295">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="f5d0c-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="f5d0c-296">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-296">Member</span></span> | <span data-ttu-id="f5d0c-297">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-298">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="f5d0c-299">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-300">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-301">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-302">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-303">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-304">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-305">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-306">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-307">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-308">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-309">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-310">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-311">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-312">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-313">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-314">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-315">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-316">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-317">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-318">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-319">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-320">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-321">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="f5d0c-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-322">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-323">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-324">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-325">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="f5d0c-326">System. Security. Cryptography. Pkcs</span><span class="sxs-lookup"><span data-stu-id="f5d0c-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="f5d0c-327">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-327">Member</span></span> | <span data-ttu-id="f5d0c-328">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="f5d0c-329">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-330">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="f5d0c-331">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="f5d0c-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="f5d0c-332">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-332">Member</span></span> | <span data-ttu-id="f5d0c-333">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-334">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-335">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-336">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-336">All</span></span> |
| <span data-ttu-id="f5d0c-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="f5d0c-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="f5d0c-338">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="f5d0c-339">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="f5d0c-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="f5d0c-340">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-340">Member</span></span> | <span data-ttu-id="f5d0c-341">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-342">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="f5d0c-343">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="f5d0c-343">System.Security.Policy</span></span>

| <span data-ttu-id="f5d0c-344">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-344">Member</span></span> | <span data-ttu-id="f5d0c-345">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-346">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="f5d0c-347">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="f5d0c-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="f5d0c-348">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-348">Member</span></span> | <span data-ttu-id="f5d0c-349">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="f5d0c-350">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="f5d0c-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="f5d0c-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="f5d0c-352">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-352">Member</span></span> | <span data-ttu-id="f5d0c-353">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-354">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="f5d0c-355">System. Threading</span><span class="sxs-lookup"><span data-stu-id="f5d0c-355">System.Threading</span></span>

| <span data-ttu-id="f5d0c-356">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-356">Member</span></span> | <span data-ttu-id="f5d0c-357">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-358">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-359">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-360">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-361">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-362">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-363">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="f5d0c-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="f5d0c-364">System.Xml</span></span>

| <span data-ttu-id="f5d0c-365">Üye</span><span class="sxs-lookup"><span data-stu-id="f5d0c-365">Member</span></span> | <span data-ttu-id="f5d0c-366">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="f5d0c-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-367">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-368">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="f5d0c-369">Tümü</span><span class="sxs-lookup"><span data-stu-id="f5d0c-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="f5d0c-370">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5d0c-370">See also</span></span>

- [<span data-ttu-id="f5d0c-371">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="f5d0c-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="f5d0c-372">.NET Core 'da ikili serileştirme</span><span class="sxs-lookup"><span data-stu-id="f5d0c-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="f5d0c-373">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="f5d0c-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
