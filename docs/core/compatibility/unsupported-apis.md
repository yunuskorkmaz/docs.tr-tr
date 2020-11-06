---
title: .NET Core ve .NET 5 + üzerinde desteklenmeyen API 'Ler
titleSuffix: ''
description: .NET API 'Lerin hangi .NET Core ve .NET 5,0 ve sonraki sürümlerinde her zaman bir istisna sağladığını öğrenin.
ms.date: 10/13/2020
ms.openlocfilehash: 51d73557a48910d9cb1c4d3cdced34dfe4d849d8
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329787"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="5d955-103">.NET Core ve .NET 5 + ' da her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="5d955-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="5d955-104">Aşağıdaki API 'Ler her zaman bir <xref:System.PlatformNotSupportedException> Platform alt kümesi üzerinde .net 5,0 ve sonraki sürümlerinde (.NET Core 'un tüm sürümleri dahil) her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d955-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="5d955-105">Bu makale, etkilenen API 'Leri ad alanına göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="5d955-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="5d955-106">Bu makale, devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="5d955-106">This article is a work-in-progress.</span></span> <span data-ttu-id="5d955-107">.NET 5 + ' da özel durum oluşturan API 'lerin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="5d955-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="5d955-108">Bu makalede, .NET 5 + ' de oluşturan ikili serileştirme için açık arabirim uygulamaları dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="5d955-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="5d955-109">Daha fazla bilgi için bkz. [.NET Core 'Da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="5d955-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="5d955-110">Sistem</span><span class="sxs-lookup"><span data-stu-id="5d955-110">System</span></span>

| <span data-ttu-id="5d955-111">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-111">Member</span></span> | <span data-ttu-id="5d955-112">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-113">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="5d955-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="5d955-115">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="5d955-116">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="5d955-118">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="5d955-119">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="5d955-120">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-121">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="5d955-122">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="5d955-123">System. CodeDom. derleyicisi</span><span class="sxs-lookup"><span data-stu-id="5d955-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="5d955-124">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-124">Member</span></span> | <span data-ttu-id="5d955-125">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-127">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-128">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="5d955-129">System. Collections. özelleşmiş</span><span class="sxs-lookup"><span data-stu-id="5d955-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="5d955-130">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-130">Member</span></span> | <span data-ttu-id="5d955-131">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-132">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="5d955-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="5d955-135">System.Configurlama</span><span class="sxs-lookup"><span data-stu-id="5d955-135">System.Configuration</span></span>

| <span data-ttu-id="5d955-136">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-136">Member</span></span> | <span data-ttu-id="5d955-137">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="5d955-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="5d955-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="5d955-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="5d955-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="5d955-140">System.Console</span></span>

| <span data-ttu-id="5d955-141">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-141">Member</span></span> | <span data-ttu-id="5d955-142">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="5d955-143">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-143">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-145">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-145">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-147">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-147">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-149">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-149">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="5d955-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="5d955-151">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-152">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-153">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-154">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-154">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-155"><xref:System.Console.Title?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="5d955-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="5d955-156">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-156">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-158">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-158">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-160">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-160">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-162">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-162">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-164">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="5d955-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="5d955-165">System.Data.Common</span></span>

| <span data-ttu-id="5d955-166">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-166">Member</span></span> | <span data-ttu-id="5d955-167">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="5d955-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (atar <xref:System.NotSupportedException> )</span><span class="sxs-lookup"><span data-stu-id="5d955-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="5d955-169">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="5d955-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="5d955-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="5d955-171">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-171">Member</span></span> | <span data-ttu-id="5d955-172">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="5d955-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-174">Linux</span><span class="sxs-lookup"><span data-stu-id="5d955-174">Linux</span></span> |
| <span data-ttu-id="5d955-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-176">Linux</span><span class="sxs-lookup"><span data-stu-id="5d955-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="5d955-177">macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="5d955-178">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-179">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="5d955-180">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="5d955-181">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="5d955-182">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="5d955-183">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-183">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-185">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-185">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="5d955-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="5d955-187">macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-187">macOS</span></span> |
| <span data-ttu-id="5d955-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-189">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="5d955-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="5d955-190">System.IO</span></span>

| <span data-ttu-id="5d955-191">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-191">Member</span></span> | <span data-ttu-id="5d955-192">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-193">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-194">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="5d955-195">System. ıO. Pipes</span><span class="sxs-lookup"><span data-stu-id="5d955-195">System.IO.Pipes</span></span>

| <span data-ttu-id="5d955-196">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-196">Member</span></span> | <span data-ttu-id="5d955-197">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="5d955-198">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="5d955-199">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="5d955-200">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="5d955-201">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-201">Linux and macOS</span></span> |
| <span data-ttu-id="5d955-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-203">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="5d955-204">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="5d955-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="5d955-205">System.Media</span></span>

| <span data-ttu-id="5d955-206">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-206">Member</span></span> | <span data-ttu-id="5d955-207">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-208">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="5d955-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="5d955-209">System.Net</span></span>

| <span data-ttu-id="5d955-210">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-210">Member</span></span> | <span data-ttu-id="5d955-211">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="5d955-212">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="5d955-213">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-214">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-215">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-216">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-217">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-218">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-219">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-220">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-221">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-222">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="5d955-223">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-224">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-225">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-226">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-227">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-228">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="5d955-229">System .net. NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="5d955-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="5d955-230">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-230">Member</span></span> | <span data-ttu-id="5d955-231">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="5d955-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="5d955-233">System .net. Sockets</span><span class="sxs-lookup"><span data-stu-id="5d955-233">System.Net.Sockets</span></span>

| <span data-ttu-id="5d955-234">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-234">Member</span></span> | <span data-ttu-id="5d955-235">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="5d955-236">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="5d955-237">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="5d955-238">System .net. WebSockets</span><span class="sxs-lookup"><span data-stu-id="5d955-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="5d955-239">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-239">Member</span></span> | <span data-ttu-id="5d955-240">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="5d955-241">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="5d955-242">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="5d955-242">System.Reflection</span></span>

| <span data-ttu-id="5d955-243">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-243">Member</span></span> | <span data-ttu-id="5d955-244">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-245">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5d955-246">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-247">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="5d955-248">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="5d955-249">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-250">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="5d955-251">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="5d955-252">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="5d955-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="5d955-253">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-253">Member</span></span> | <span data-ttu-id="5d955-254">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="5d955-255">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="5d955-256">System. Runtime. InteropServices</span><span class="sxs-lookup"><span data-stu-id="5d955-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="5d955-257">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-257">Member</span></span> | <span data-ttu-id="5d955-258">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="5d955-259">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="5d955-260">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="5d955-261">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="5d955-262">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5d955-263">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="5d955-264">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="5d955-265">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="5d955-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="5d955-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="5d955-267">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-267">Member</span></span> | <span data-ttu-id="5d955-268">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="5d955-269">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="5d955-270">System. Security</span><span class="sxs-lookup"><span data-stu-id="5d955-270">System.Security</span></span>

| <span data-ttu-id="5d955-271">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-271">Member</span></span> | <span data-ttu-id="5d955-272">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="5d955-273">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="5d955-274">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="5d955-275">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="5d955-276">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="5d955-277">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="5d955-278">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="5d955-279">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="5d955-280">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="5d955-281">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="5d955-282">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="5d955-283">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="5d955-284">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="5d955-285">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="5d955-286">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="5d955-287">System. Security. Claim</span><span class="sxs-lookup"><span data-stu-id="5d955-287">System.Security.Claims</span></span>

| <span data-ttu-id="5d955-288">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-288">Member</span></span> | <span data-ttu-id="5d955-289">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-290">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-291">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="5d955-292">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-293">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-294">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="5d955-295">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="5d955-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="5d955-296">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-296">Member</span></span> | <span data-ttu-id="5d955-297">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5d955-298">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="5d955-299">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="5d955-300">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="5d955-301">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="5d955-302">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="5d955-303">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="5d955-304">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="5d955-305">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="5d955-306">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="5d955-307">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="5d955-308">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="5d955-309">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="5d955-310">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="5d955-311">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="5d955-312">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="5d955-313">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5d955-314">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-315">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-316">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-317">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="5d955-318">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5d955-319">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-320">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-321">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="5d955-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-322">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-323">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="5d955-324">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5d955-325">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="5d955-326">System. Security. Cryptography. Pkcs</span><span class="sxs-lookup"><span data-stu-id="5d955-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="5d955-327">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-327">Member</span></span> | <span data-ttu-id="5d955-328">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="5d955-329">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="5d955-330">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="5d955-331">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="5d955-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="5d955-332">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-332">Member</span></span> | <span data-ttu-id="5d955-333">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-334">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-335">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-336">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-336">All</span></span> |
| <span data-ttu-id="5d955-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="5d955-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5d955-338">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="5d955-339">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="5d955-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="5d955-340">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-340">Member</span></span> | <span data-ttu-id="5d955-341">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-342">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="5d955-343">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="5d955-343">System.Security.Policy</span></span>

| <span data-ttu-id="5d955-344">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-344">Member</span></span> | <span data-ttu-id="5d955-345">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-346">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="5d955-347">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="5d955-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="5d955-348">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-348">Member</span></span> | <span data-ttu-id="5d955-349">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5d955-350">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="5d955-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="5d955-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="5d955-352">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-352">Member</span></span> | <span data-ttu-id="5d955-353">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-354">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="5d955-355">System. Threading</span><span class="sxs-lookup"><span data-stu-id="5d955-355">System.Threading</span></span>

| <span data-ttu-id="5d955-356">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-356">Member</span></span> | <span data-ttu-id="5d955-357">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-358">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5d955-359">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="5d955-360">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="5d955-361">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="5d955-362">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="5d955-363">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="5d955-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="5d955-364">System.Xml</span></span>

| <span data-ttu-id="5d955-365">Üye</span><span class="sxs-lookup"><span data-stu-id="5d955-365">Member</span></span> | <span data-ttu-id="5d955-366">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="5d955-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="5d955-367">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="5d955-368">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="5d955-369">Tümü</span><span class="sxs-lookup"><span data-stu-id="5d955-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="5d955-370">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d955-370">See also</span></span>

- [<span data-ttu-id="5d955-371">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="5d955-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="5d955-372">.NET Core 'da ikili serileştirme</span><span class="sxs-lookup"><span data-stu-id="5d955-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="5d955-373">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="5d955-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
