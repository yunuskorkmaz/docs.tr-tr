---
title: .NET Core ve .NET 5 + üzerinde desteklenmeyen API 'Ler
titleSuffix: ''
description: .NET API 'Lerinin her zaman .NET Core ve .NET 5 ve sonraki sürümlerde bir istisna oluşturmasını öğrenin.
ms.date: 10/13/2020
ms.openlocfilehash: b0dc425bf5f7d8f2a44f51ffe75ffcb0c8a5a7ae
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256263"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="a2725-103">.NET Core ve .NET 5 + ' da her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="a2725-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="a2725-104">Aşağıdaki API 'Ler her zaman bir <xref:System.PlatformNotSupportedException> Platform alt kümesi üzerinde .NET 5 ve sonraki sürümleri (.NET Core 'un tüm sürümleri dahil) üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a2725-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="a2725-105">Bu makale, etkilenen API 'Leri ad alanına göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="a2725-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="a2725-106">Bu makale, devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="a2725-106">This article is a work-in-progress.</span></span> <span data-ttu-id="a2725-107">.NET 5 + ' da özel durum oluşturan API 'lerin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="a2725-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="a2725-108">Bu makalede, .NET 5 + ' de oluşturan ikili serileştirme için açık arabirim uygulamaları dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="a2725-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="a2725-109">Daha fazla bilgi için bkz. [.NET Core 'Da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="a2725-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="a2725-110">Sistem</span><span class="sxs-lookup"><span data-stu-id="a2725-110">System</span></span>

| <span data-ttu-id="a2725-111">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-111">Member</span></span> | <span data-ttu-id="a2725-112">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-113">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="a2725-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="a2725-115">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="a2725-116">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="a2725-118">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="a2725-119">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="a2725-120">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-121">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="a2725-122">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="a2725-123">System. CodeDom. derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a2725-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="a2725-124">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-124">Member</span></span> | <span data-ttu-id="a2725-125">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-127">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-128">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="a2725-129">System. Collections. özelleşmiş</span><span class="sxs-lookup"><span data-stu-id="a2725-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="a2725-130">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-130">Member</span></span> | <span data-ttu-id="a2725-131">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-132">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a2725-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="a2725-135">System.Configurlama</span><span class="sxs-lookup"><span data-stu-id="a2725-135">System.Configuration</span></span>

| <span data-ttu-id="a2725-136">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-136">Member</span></span> | <span data-ttu-id="a2725-137">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="a2725-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="a2725-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="a2725-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="a2725-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="a2725-140">System.Console</span></span>

| <span data-ttu-id="a2725-141">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-141">Member</span></span> | <span data-ttu-id="a2725-142">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="a2725-143">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-143">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-145">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-145">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-147">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-147">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-149">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-149">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="a2725-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="a2725-151">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-152">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-153">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-154">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-154">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-155"><xref:System.Console.Title?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="a2725-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="a2725-156">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-156">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-158">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-158">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-160">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-160">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-162">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-162">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-164">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="a2725-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="a2725-165">System.Data.Common</span></span>

| <span data-ttu-id="a2725-166">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-166">Member</span></span> | <span data-ttu-id="a2725-167">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="a2725-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (atar <xref:System.NotSupportedException> )</span><span class="sxs-lookup"><span data-stu-id="a2725-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="a2725-169">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="a2725-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="a2725-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="a2725-171">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-171">Member</span></span> | <span data-ttu-id="a2725-172">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="a2725-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-174">Linux</span><span class="sxs-lookup"><span data-stu-id="a2725-174">Linux</span></span> |
| <span data-ttu-id="a2725-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-176">Linux</span><span class="sxs-lookup"><span data-stu-id="a2725-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="a2725-177">macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="a2725-178">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="a2725-179">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="a2725-180">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="a2725-181">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="a2725-182">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="a2725-183">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-183">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="a2725-184">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-184">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-186">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-186">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca Get)</span><span class="sxs-lookup"><span data-stu-id="a2725-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="a2725-188">Mac OS</span><span class="sxs-lookup"><span data-stu-id="a2725-188">macOS</span></span> |
| <span data-ttu-id="a2725-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-190">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-190">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="a2725-191">System.IO</span><span class="sxs-lookup"><span data-stu-id="a2725-191">System.IO</span></span>

| <span data-ttu-id="a2725-192">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-192">Member</span></span> | <span data-ttu-id="a2725-193">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-193">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-194">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-194">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-195">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-195">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="a2725-196">System. ıO. Pipes</span><span class="sxs-lookup"><span data-stu-id="a2725-196">System.IO.Pipes</span></span>

| <span data-ttu-id="a2725-197">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-197">Member</span></span> | <span data-ttu-id="a2725-198">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-198">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="a2725-199">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="a2725-200">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="a2725-201">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-201">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="a2725-202">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-202">Linux and macOS</span></span> |
| <span data-ttu-id="a2725-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-204">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-204">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="a2725-205">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-205">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="a2725-206">System. Media</span><span class="sxs-lookup"><span data-stu-id="a2725-206">System.Media</span></span>

| <span data-ttu-id="a2725-207">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-207">Member</span></span> | <span data-ttu-id="a2725-208">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-208">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-209">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-209">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="a2725-210">System.Net</span><span class="sxs-lookup"><span data-stu-id="a2725-210">System.Net</span></span>

| <span data-ttu-id="a2725-211">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-211">Member</span></span> | <span data-ttu-id="a2725-212">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-212">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="a2725-213">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-213">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="a2725-214">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-214">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-215">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-215">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-216">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-216">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-217">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-217">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-218">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-219">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-219">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-220">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-221">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-221">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-222">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-222">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-223">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-223">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="a2725-224">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-224">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-225">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-225">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-226">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-226">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-227">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-227">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-228">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-228">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-229">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-229">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="a2725-230">System .net. NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="a2725-230">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="a2725-231">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-231">Member</span></span> | <span data-ttu-id="a2725-232">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-232">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-233">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="a2725-233">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="a2725-234">System .net. Sockets</span><span class="sxs-lookup"><span data-stu-id="a2725-234">System.Net.Sockets</span></span>

| <span data-ttu-id="a2725-235">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-235">Member</span></span> | <span data-ttu-id="a2725-236">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-236">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="a2725-237">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-237">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="a2725-238">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-238">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="a2725-239">System .net. WebSockets</span><span class="sxs-lookup"><span data-stu-id="a2725-239">System.Net.WebSockets</span></span>

| <span data-ttu-id="a2725-240">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-240">Member</span></span> | <span data-ttu-id="a2725-241">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-241">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="a2725-242">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-242">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="a2725-243">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="a2725-243">System.Reflection</span></span>

| <span data-ttu-id="a2725-244">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-244">Member</span></span> | <span data-ttu-id="a2725-245">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-245">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-246">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-246">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a2725-247">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-248">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-248">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a2725-249">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="a2725-250">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-251">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-251">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="a2725-252">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-252">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="a2725-253">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="a2725-253">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="a2725-254">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-254">Member</span></span> | <span data-ttu-id="a2725-255">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-255">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="a2725-256">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-256">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="a2725-257">System. Runtime. InteropServices</span><span class="sxs-lookup"><span data-stu-id="a2725-257">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="a2725-258">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-258">Member</span></span> | <span data-ttu-id="a2725-259">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-259">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a2725-260">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="a2725-261">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="a2725-262">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-262">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="a2725-263">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-263">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a2725-264">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="a2725-265">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-265">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="a2725-266">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-266">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="a2725-267">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="a2725-267">System.Runtime.Serialization</span></span>

| <span data-ttu-id="a2725-268">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-268">Member</span></span> | <span data-ttu-id="a2725-269">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-269">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="a2725-270">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-270">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="a2725-271">System. Security</span><span class="sxs-lookup"><span data-stu-id="a2725-271">System.Security</span></span>

| <span data-ttu-id="a2725-272">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-272">Member</span></span> | <span data-ttu-id="a2725-273">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-273">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="a2725-274">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-274">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="a2725-275">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-275">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="a2725-276">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-276">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="a2725-277">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-277">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="a2725-278">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-278">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="a2725-279">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-279">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="a2725-280">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-280">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="a2725-281">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="a2725-282">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-282">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="a2725-283">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-283">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="a2725-284">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-284">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a2725-285">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="a2725-286">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-286">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="a2725-287">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-287">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="a2725-288">System. Security. Claim</span><span class="sxs-lookup"><span data-stu-id="a2725-288">System.Security.Claims</span></span>

| <span data-ttu-id="a2725-289">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-289">Member</span></span> | <span data-ttu-id="a2725-290">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-290">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-291">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-292">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="a2725-293">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-294">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-294">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-295">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-295">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="a2725-296">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="a2725-296">System.Security.Cryptography</span></span>

| <span data-ttu-id="a2725-297">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-297">Member</span></span> | <span data-ttu-id="a2725-298">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-298">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a2725-299">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-299">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="a2725-300">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="a2725-301">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="a2725-302">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="a2725-303">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="a2725-304">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="a2725-305">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="a2725-306">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="a2725-307">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="a2725-308">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="a2725-309">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="a2725-310">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="a2725-311">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="a2725-312">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-312">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="a2725-313">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="a2725-314">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a2725-315">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-316">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-317">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-317">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-318">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="a2725-319">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-319">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a2725-320">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-320">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-321">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-322">Linux ve macOS</span><span class="sxs-lookup"><span data-stu-id="a2725-322">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-323">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-323">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-324">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="a2725-325">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-325">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a2725-326">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-326">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="a2725-327">System. Security. Cryptography. Pkcs</span><span class="sxs-lookup"><span data-stu-id="a2725-327">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="a2725-328">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-328">Member</span></span> | <span data-ttu-id="a2725-329">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-329">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="a2725-330">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="a2725-331">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="a2725-332">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="a2725-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="a2725-333">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-333">Member</span></span> | <span data-ttu-id="a2725-334">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-335">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-336">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-337">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-337">All</span></span> |
| <span data-ttu-id="a2725-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (yalnızca set)</span><span class="sxs-lookup"><span data-stu-id="a2725-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a2725-339">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="a2725-340">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="a2725-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="a2725-341">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-341">Member</span></span> | <span data-ttu-id="a2725-342">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-343">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="a2725-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="a2725-344">System.Security.Policy</span></span>

| <span data-ttu-id="a2725-345">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-345">Member</span></span> | <span data-ttu-id="a2725-346">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-347">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="a2725-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="a2725-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="a2725-349">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-349">Member</span></span> | <span data-ttu-id="a2725-350">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a2725-351">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="a2725-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="a2725-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="a2725-353">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-353">Member</span></span> | <span data-ttu-id="a2725-354">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-355">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="a2725-356">System. Threading</span><span class="sxs-lookup"><span data-stu-id="a2725-356">System.Threading</span></span>

| <span data-ttu-id="a2725-357">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-357">Member</span></span> | <span data-ttu-id="a2725-358">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-359">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a2725-360">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="a2725-361">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="a2725-362">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="a2725-363">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="a2725-364">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="a2725-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="a2725-365">System.Xml</span></span>

| <span data-ttu-id="a2725-366">Üye</span><span class="sxs-lookup"><span data-stu-id="a2725-366">Member</span></span> | <span data-ttu-id="a2725-367">Oluşturan platformlar</span><span class="sxs-lookup"><span data-stu-id="a2725-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="a2725-368">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="a2725-369">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="a2725-370">Tümü</span><span class="sxs-lookup"><span data-stu-id="a2725-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="a2725-371">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2725-371">See also</span></span>

- [<span data-ttu-id="a2725-372">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="a2725-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="a2725-373">.NET Core 'da ikili serileştirme</span><span class="sxs-lookup"><span data-stu-id="a2725-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="a2725-374">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="a2725-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
