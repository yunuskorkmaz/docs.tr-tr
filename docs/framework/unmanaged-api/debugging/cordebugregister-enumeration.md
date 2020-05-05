---
title: CorDebugRegister Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
ms.openlocfilehash: 19d0dcf8a5633371765861fcc29df4ef8c91ebc4
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795722"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="380e5-102">CorDebugRegister Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="380e5-102">CorDebugRegister Enumeration</span></span>
<span data-ttu-id="380e5-103">Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.</span><span class="sxs-lookup"><span data-stu-id="380e5-103">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="380e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="380e5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a><span data-ttu-id="380e5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="380e5-105">Members</span></span>  
  
|<span data-ttu-id="380e5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="380e5-106">Member</span></span>|<span data-ttu-id="380e5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="380e5-107">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="380e5-108">Bir yönerge işaretçisi herhangi bir işlemciye kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-108">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="380e5-109">Yığın işaretçisi herhangi bir işlemciye kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-109">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="380e5-110">Bir çerçeve işaretçisi herhangi bir işlemciye kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-110">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="380e5-111">Yönerge işaretçisi x86 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-111">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="380e5-112">Yığın işaretçisi x86 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-112">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="380e5-113">Temel işaretçi x86 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-113">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="380e5-114">X86 işlemcisinde bir veri kaydı.</span><span class="sxs-lookup"><span data-stu-id="380e5-114">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="380e5-115">C verileri x86 işlemcisine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="380e5-115">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="380e5-116">D verileri x86 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-116">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="380e5-117">B verileri x86 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-117">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="380e5-118">Kaynak dizin, x86 işlemcide kayıt yaptırın.</span><span class="sxs-lookup"><span data-stu-id="380e5-118">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="380e5-119">Hedef dizin, x86 işlemcide kayıt yaptırın.</span><span class="sxs-lookup"><span data-stu-id="380e5-119">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="380e5-120">Yığın, x86 kayan nokta (FP) işlemcisinde 0 ' ı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-120">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="380e5-121">#1 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-121">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="380e5-122">#2 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-122">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="380e5-123">#3 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-123">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="380e5-124">#4 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-124">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="380e5-125">#5 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-125">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="380e5-126">#6 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-126">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="380e5-127">#7 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-127">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="380e5-128">Yönerge işaretçisi AMD64 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-128">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="380e5-129">Yığın işaretçisi AMD64 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-129">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="380e5-130">Temel işaretçi AMD64 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-130">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="380e5-131">AMD64 işlemcisinde bir veri kaydı.</span><span class="sxs-lookup"><span data-stu-id="380e5-131">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="380e5-132">C verileri AMD64 işlemcisine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="380e5-132">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="380e5-133">D verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-133">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="380e5-134">B verileri AMD64 işlemci üzerinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-134">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="380e5-135">Kaynak dizini AMD64 işlemcide kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-135">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="380e5-136">Hedef dizin AMD64 işlemci üzerinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-136">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="380e5-137">#8 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-137">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="380e5-138">#9 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-138">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="380e5-139">#10 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-139">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="380e5-140">#11 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-140">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="380e5-141">#12 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-141">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="380e5-142">#13 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-142">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="380e5-143">#14 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-143">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="380e5-144">#15 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-144">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="380e5-145">#0 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-145">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="380e5-146">#1 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-146">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="380e5-147">#2 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-147">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="380e5-148">#3 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-148">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="380e5-149">#4 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-149">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="380e5-150">#5 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-150">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="380e5-151">#6 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-151">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="380e5-152">#7 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-152">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="380e5-153">#8 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-153">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="380e5-154">#9 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-154">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="380e5-155">#10 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-155">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="380e5-156">#11 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-156">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="380e5-157">#12 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-157">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="380e5-158">#13 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-158">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="380e5-159">#14 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-159">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="380e5-160">#15 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="380e5-160">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="380e5-161">Yığın işaretçisi, IA-64 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-161">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="380e5-162">#0 veri, IA-64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="380e5-162">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="380e5-163">#0, IA-64 işlemcisinde FP veri kaydı.</span><span class="sxs-lookup"><span data-stu-id="380e5-163">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="380e5-164">ARM işlemcisinde program sayaç kaydı (R15).</span><span class="sxs-lookup"><span data-stu-id="380e5-164">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="380e5-165">Yığın işaretçisi, ARM işlemcisinde kayıt (R13).</span><span class="sxs-lookup"><span data-stu-id="380e5-165">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="380e5-166">ARM işlemcisinde veri kaydı R0.</span><span class="sxs-lookup"><span data-stu-id="380e5-166">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="380e5-167">ARM işlemcisinde veri kaydı R1.</span><span class="sxs-lookup"><span data-stu-id="380e5-167">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="380e5-168">ARM işlemcisinde veri kayıt R2.</span><span class="sxs-lookup"><span data-stu-id="380e5-168">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="380e5-169">ARM işlemcisinde veri kaydı R3.</span><span class="sxs-lookup"><span data-stu-id="380e5-169">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="380e5-170">ARM işlemcisine R4 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-170">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="380e5-171">ARM işlemcisine R5 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-171">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="380e5-172">ARM işlemcisine R6 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-172">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="380e5-173">ARM işlemcisine R7 (THUMB kare işaretçisi) öğesini kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="380e5-173">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="380e5-174">ARM işlemcisine R8 öğesini kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="380e5-174">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="380e5-175">ARM işlemcisine R9 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-175">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="380e5-176">ARM işlemcisine R10 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-176">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="380e5-177">ARM işlemcisindeki çerçeve işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="380e5-177">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="380e5-178">ARM işlemcisine R12 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="380e5-178">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="380e5-179">ARM işlemcisinde bağlantı yazmacı (R14).</span><span class="sxs-lookup"><span data-stu-id="380e5-179">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="380e5-180">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="380e5-180">Remarks</span></span>  
 <span data-ttu-id="380e5-181">IA-64 işlemcisinde 128 genel amaçlı veri kayıtları ve 128 kayan nokta veri kayıtları vardır ancak yalnızca değerler `REGISTER_IA64_R0` ve `REGISTER_IA64_F0` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="380e5-181">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="380e5-182">Diğer değerler aşağıdaki şekilde belirlenebilir:</span><span class="sxs-lookup"><span data-stu-id="380e5-182">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="380e5-183">IA-64 işlemcisinde #127 `REGISTER_IA64_R0` veri kaydı `REGISTER_IA64_R1` aracılığıyla `REGISTER_IA64_R127`#1 veri kaydına karşılık gelen değerler için kayıt numarasını öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="380e5-183">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="380e5-184">, IA-64 işlemcisinde `REGISTER_IA64_F0` #127 FP `REGISTER_IA64_F1` VERI `REGISTER_IA64_F127`kaydı aracılığıyla #1 FP veri kaydına karşılık gelen değerler için kayıt numarasını öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="380e5-184">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="380e5-185">Örneğin, IA-64 işlemcisinde #83 veri kaydını belirtmeniz gerekiyorsa + 83 kullanın `REGISTER_IA64_R0` .</span><span class="sxs-lookup"><span data-stu-id="380e5-185">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="380e5-186">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="380e5-186">Requirements</span></span>  
 <span data-ttu-id="380e5-187">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="380e5-187">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="380e5-188">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="380e5-188">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="380e5-189">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="380e5-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="380e5-190">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="380e5-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="380e5-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="380e5-191">See also</span></span>

- [<span data-ttu-id="380e5-192">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="380e5-192">Debugging Enumerations</span></span>](debugging-enumerations.md)
