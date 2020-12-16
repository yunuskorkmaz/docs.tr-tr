---
title: .NET Core ve .NET 5 + üzerinde desteklenmeyen API 'Ler
titleSuffix: ''
description: .NET API 'Lerin hangi .NET Core ve .NET 5,0 ve sonraki sürümlerinde her zaman bir istisna sağladığını öğrenin.
ms.date: 10/13/2020
ms.openlocfilehash: 1bd41192d0d6752d2b659da9fb6387dac321b2c3
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593272"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="7d7ba-103">.NET Core ve .NET 5 + ' da her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="7d7ba-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="7d7ba-104">Aşağıdaki API 'Ler her zaman bir <xref:System.PlatformNotSupportedException> Platform alt kümesi üzerinde .net 5,0 ve sonraki sürümlerinde (.NET Core 'un tüm sürümleri dahil) her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7d7ba-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="7d7ba-105">Bu makale, etkilenen API 'Leri ad alanına göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="7d7ba-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="7d7ba-106">Bu makale, devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="7d7ba-106">This article is a work-in-progress.</span></span> <span data-ttu-id="7d7ba-107">.NET 5 + ' da özel durum oluşturan API 'lerin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="7d7ba-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="7d7ba-108">Bu makalede, .NET 5 + ' de oluşturan ikili serileştirme için açık arabirim uygulamaları dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="7d7ba-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="7d7ba-109">Daha fazla bilgi için bkz. [.NET Core 'Da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="7d7ba-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="7d7ba-110">Sistem</span><span class="sxs-lookup"><span data-stu-id="7d7ba-110">System</span></span>

| <span data-ttu-id="7d7ba-111">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-111">Member</span></span> | <span data-ttu-id="7d7ba-112">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-113">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-115">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-116">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-118">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-119">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-120">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-121">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-122">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="7d7ba-123">System. CodeDom. derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7d7ba-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="7d7ba-124">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-124">Member</span></span> | <span data-ttu-id="7d7ba-125">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-127">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-128">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="7d7ba-129">System. Collections. özelleşmiş</span><span class="sxs-lookup"><span data-stu-id="7d7ba-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="7d7ba-130">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-130">Member</span></span> | <span data-ttu-id="7d7ba-131">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-132">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="7d7ba-135">System.Configurlama</span><span class="sxs-lookup"><span data-stu-id="7d7ba-135">System.Configuration</span></span>

| <span data-ttu-id="7d7ba-136">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-136">Member</span></span> | <span data-ttu-id="7d7ba-137">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="7d7ba-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="7d7ba-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="7d7ba-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="7d7ba-140">System.Console</span></span>

| <span data-ttu-id="7d7ba-141">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-141">Member</span></span> | <span data-ttu-id="7d7ba-142">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-143">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-143">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-145">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-145">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-147">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-147">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-149">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-149">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="7d7ba-151">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-152">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-153">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-154">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-154">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-155"><xref:System.Console.Title?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="7d7ba-156">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-156">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-158">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-158">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-160">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-160">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-162">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-162">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-164">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="7d7ba-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="7d7ba-165">System.Data.Common</span></span>

| <span data-ttu-id="7d7ba-166">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-166">Member</span></span> | <span data-ttu-id="7d7ba-167">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="7d7ba-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (atar <xref:System.NotSupportedException> )</span><span class="sxs-lookup"><span data-stu-id="7d7ba-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="7d7ba-169">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="7d7ba-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="7d7ba-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="7d7ba-171">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-171">Member</span></span> | <span data-ttu-id="7d7ba-172">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="7d7ba-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-174">Linux</span><span class="sxs-lookup"><span data-stu-id="7d7ba-174">Linux</span></span> |
| <span data-ttu-id="7d7ba-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-176">Linux</span><span class="sxs-lookup"><span data-stu-id="7d7ba-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-177">macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-178">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-179">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-180">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-181">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-182">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-183">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-183">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-184">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-184">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-186">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-186">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="7d7ba-188">macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-188">macOS</span></span> |
| <span data-ttu-id="7d7ba-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-190">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-190">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="7d7ba-191">System.IO</span><span class="sxs-lookup"><span data-stu-id="7d7ba-191">System.IO</span></span>

| <span data-ttu-id="7d7ba-192">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-192">Member</span></span> | <span data-ttu-id="7d7ba-193">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-193">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-194">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-194">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-195">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-195">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="7d7ba-196">System. ıO. Pipes</span><span class="sxs-lookup"><span data-stu-id="7d7ba-196">System.IO.Pipes</span></span>

| <span data-ttu-id="7d7ba-197">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-197">Member</span></span> | <span data-ttu-id="7d7ba-198">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-198">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-199">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-200">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-201">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-201">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-202">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-202">Linux and macOS</span></span> |
| <span data-ttu-id="7d7ba-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-204">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-204">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-205">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-205">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="7d7ba-206">System. Media</span><span class="sxs-lookup"><span data-stu-id="7d7ba-206">System.Media</span></span>

| <span data-ttu-id="7d7ba-207">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-207">Member</span></span> | <span data-ttu-id="7d7ba-208">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-208">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-209">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-209">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="7d7ba-210">System.Net</span><span class="sxs-lookup"><span data-stu-id="7d7ba-210">System.Net</span></span>

| <span data-ttu-id="7d7ba-211">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-211">Member</span></span> | <span data-ttu-id="7d7ba-212">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-212">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-213">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-213">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-214">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-214">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-215">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-215">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-216">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-216">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-217">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-217">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-218">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-219">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-219">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-220">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-221">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-221">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-222">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-222">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-223">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-223">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-224">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-224">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-225">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-225">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-226">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-226">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-227">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-227">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-228">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-228">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-229">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-229">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="7d7ba-230">System .net. NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="7d7ba-230">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="7d7ba-231">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-231">Member</span></span> | <span data-ttu-id="7d7ba-232">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-232">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-233">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-233">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="7d7ba-234">System .net. Sockets</span><span class="sxs-lookup"><span data-stu-id="7d7ba-234">System.Net.Sockets</span></span>

| <span data-ttu-id="7d7ba-235">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-235">Member</span></span> | <span data-ttu-id="7d7ba-236">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-236">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="7d7ba-237">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-237">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-238">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-238">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="7d7ba-239">System .net. WebSockets</span><span class="sxs-lookup"><span data-stu-id="7d7ba-239">System.Net.WebSockets</span></span>

| <span data-ttu-id="7d7ba-240">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-240">Member</span></span> | <span data-ttu-id="7d7ba-241">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-241">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-242">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-242">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="7d7ba-243">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="7d7ba-243">System.Reflection</span></span>

| <span data-ttu-id="7d7ba-244">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-244">Member</span></span> | <span data-ttu-id="7d7ba-245">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-245">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-246">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-246">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-247">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-248">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-248">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-249">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="7d7ba-250">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-251">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-251">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-252">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-252">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="7d7ba-253">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="7d7ba-253">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="7d7ba-254">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-254">Member</span></span> | <span data-ttu-id="7d7ba-255">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-255">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-256">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-256">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="7d7ba-257">System. Runtime. InteropServices</span><span class="sxs-lookup"><span data-stu-id="7d7ba-257">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="7d7ba-258">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-258">Member</span></span> | <span data-ttu-id="7d7ba-259">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-259">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-260">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-261">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-262">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-262">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-263">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-263">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-264">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-265">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-265">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-266">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-266">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="7d7ba-267">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="7d7ba-267">System.Runtime.Serialization</span></span>

| <span data-ttu-id="7d7ba-268">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-268">Member</span></span> | <span data-ttu-id="7d7ba-269">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-269">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-270">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-270">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="7d7ba-271">System. Security</span><span class="sxs-lookup"><span data-stu-id="7d7ba-271">System.Security</span></span>

| <span data-ttu-id="7d7ba-272">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-272">Member</span></span> | <span data-ttu-id="7d7ba-273">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-273">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-274">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-274">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-275">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-275">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-276">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-276">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-277">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-277">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-278">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-278">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-279">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-279">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-280">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-280">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-281">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-282">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-282">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-283">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-283">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-284">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-284">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-285">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-286">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-286">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-287">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-287">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="7d7ba-288">System. Security. Claim</span><span class="sxs-lookup"><span data-stu-id="7d7ba-288">System.Security.Claims</span></span>

| <span data-ttu-id="7d7ba-289">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-289">Member</span></span> | <span data-ttu-id="7d7ba-290">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-290">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-291">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-292">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="7d7ba-293">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-294">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-294">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-295">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-295">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="7d7ba-296">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="7d7ba-296">System.Security.Cryptography</span></span>

| <span data-ttu-id="7d7ba-297">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-297">Member</span></span> | <span data-ttu-id="7d7ba-298">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-298">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-299">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-299">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="7d7ba-300">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-301">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-302">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-303">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-304">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-305">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-306">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-307">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-308">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-309">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-310">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-311">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-312">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-312">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-313">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-314">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-315">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-316">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-317">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-317">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-318">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-319">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-319">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-320">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-320">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-321">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-322">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="7d7ba-322">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-323">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-323">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-324">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-325">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-325">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-326">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-326">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="7d7ba-327">System. Security. Cryptography. Pkcs</span><span class="sxs-lookup"><span data-stu-id="7d7ba-327">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="7d7ba-328">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-328">Member</span></span> | <span data-ttu-id="7d7ba-329">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-329">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="7d7ba-330">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-331">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="7d7ba-332">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="7d7ba-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="7d7ba-333">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-333">Member</span></span> | <span data-ttu-id="7d7ba-334">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-335">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-336">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-337">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-337">All</span></span> |
| <span data-ttu-id="7d7ba-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="7d7ba-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="7d7ba-339">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="7d7ba-340">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="7d7ba-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="7d7ba-341">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-341">Member</span></span> | <span data-ttu-id="7d7ba-342">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-343">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="7d7ba-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="7d7ba-344">System.Security.Policy</span></span>

| <span data-ttu-id="7d7ba-345">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-345">Member</span></span> | <span data-ttu-id="7d7ba-346">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-347">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="7d7ba-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="7d7ba-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="7d7ba-349">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-349">Member</span></span> | <span data-ttu-id="7d7ba-350">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="7d7ba-351">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="7d7ba-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="7d7ba-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="7d7ba-353">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-353">Member</span></span> | <span data-ttu-id="7d7ba-354">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-355">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="7d7ba-356">System. Threading</span><span class="sxs-lookup"><span data-stu-id="7d7ba-356">System.Threading</span></span>

| <span data-ttu-id="7d7ba-357">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-357">Member</span></span> | <span data-ttu-id="7d7ba-358">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-359">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-360">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-361">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-362">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-363">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-364">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="7d7ba-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="7d7ba-365">System.Xml</span></span>

| <span data-ttu-id="7d7ba-366">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7ba-366">Member</span></span> | <span data-ttu-id="7d7ba-367">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="7d7ba-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-368">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-369">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="7d7ba-370">Tümü</span><span class="sxs-lookup"><span data-stu-id="7d7ba-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="7d7ba-371">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d7ba-371">See also</span></span>

- [<span data-ttu-id="7d7ba-372">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="7d7ba-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="7d7ba-373">.NET Core 'da ikili serileştirme</span><span class="sxs-lookup"><span data-stu-id="7d7ba-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="7d7ba-374">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="7d7ba-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
