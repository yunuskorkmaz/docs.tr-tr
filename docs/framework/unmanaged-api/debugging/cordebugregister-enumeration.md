---
description: 'Daha fazla bilgi edinin: CorDebugRegister numaralandırması'
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
ms.openlocfilehash: 7a5dc771a239a82448f898e2f518e920993ec35a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661896"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="a8a57-103">CorDebugRegister Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a8a57-103">CorDebugRegister Enumeration</span></span>

<span data-ttu-id="a8a57-104">Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8a57-104">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8a57-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8a57-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a8a57-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a8a57-106">Members</span></span>  
  
|<span data-ttu-id="a8a57-107">Üye</span><span class="sxs-lookup"><span data-stu-id="a8a57-107">Member</span></span>|<span data-ttu-id="a8a57-108">Description</span><span class="sxs-lookup"><span data-stu-id="a8a57-108">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="a8a57-109">Bir yönerge işaretçisi herhangi bir işlemciye kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-109">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="a8a57-110">Yığın işaretçisi herhangi bir işlemciye kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-110">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="a8a57-111">Bir çerçeve işaretçisi herhangi bir işlemciye kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-111">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="a8a57-112">Yönerge işaretçisi x86 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-112">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="a8a57-113">Yığın işaretçisi x86 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-113">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="a8a57-114">Temel işaretçi x86 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-114">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="a8a57-115">X86 işlemcisinde bir veri kaydı.</span><span class="sxs-lookup"><span data-stu-id="a8a57-115">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="a8a57-116">C verileri x86 işlemcisine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a8a57-116">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="a8a57-117">D verileri x86 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-117">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="a8a57-118">B verileri x86 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-118">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="a8a57-119">Kaynak dizin, x86 işlemcide kayıt yaptırın.</span><span class="sxs-lookup"><span data-stu-id="a8a57-119">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="a8a57-120">Hedef dizin, x86 işlemcide kayıt yaptırın.</span><span class="sxs-lookup"><span data-stu-id="a8a57-120">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="a8a57-121">Yığın, x86 kayan nokta (FP) işlemcisinde 0 ' ı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-121">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="a8a57-122">#1 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-122">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="a8a57-123">#2 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-123">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="a8a57-124">#3 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-124">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="a8a57-125">#4 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-125">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="a8a57-126">#5 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-126">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="a8a57-127">#6 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-127">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="a8a57-128">#7 Stack, x86 FP işlemcisine kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-128">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="a8a57-129">Yönerge işaretçisi AMD64 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-129">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="a8a57-130">Yığın işaretçisi AMD64 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-130">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="a8a57-131">Temel işaretçi AMD64 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-131">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="a8a57-132">AMD64 işlemcisinde bir veri kaydı.</span><span class="sxs-lookup"><span data-stu-id="a8a57-132">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="a8a57-133">C verileri AMD64 işlemcisine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a8a57-133">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="a8a57-134">D verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-134">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="a8a57-135">B verileri AMD64 işlemci üzerinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-135">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="a8a57-136">Kaynak dizini AMD64 işlemcide kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-136">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="a8a57-137">Hedef dizin AMD64 işlemci üzerinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-137">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="a8a57-138">#8 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-138">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="a8a57-139">#9 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-139">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="a8a57-140">#10 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-140">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="a8a57-141">#11 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-141">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="a8a57-142">#12 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-142">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="a8a57-143">#13 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-143">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="a8a57-144">#14 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-144">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="a8a57-145">#15 verileri AMD64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-145">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="a8a57-146">#0 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-146">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="a8a57-147">#1 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-147">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="a8a57-148">#2 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-148">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="a8a57-149">#3 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-149">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="a8a57-150">#4 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-150">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="a8a57-151">#5 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-151">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="a8a57-152">#6 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-152">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="a8a57-153">#7 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-153">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="a8a57-154">#8 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-154">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="a8a57-155">#9 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-155">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="a8a57-156">#10 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-156">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="a8a57-157">#11 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-157">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="a8a57-158">#12 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-158">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="a8a57-159">#13 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-159">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="a8a57-160">#14 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-160">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="a8a57-161">#15 multimedyayı AMD64 işlemcisine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8a57-161">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="a8a57-162">Yığın işaretçisi, IA-64 işlemcisine kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-162">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="a8a57-163">#0 veri, IA-64 işlemcisinde kayıt.</span><span class="sxs-lookup"><span data-stu-id="a8a57-163">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="a8a57-164">#0, IA-64 işlemcisinde FP veri kaydı.</span><span class="sxs-lookup"><span data-stu-id="a8a57-164">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="a8a57-165">ARM işlemcisinde program sayaç kaydı (R15).</span><span class="sxs-lookup"><span data-stu-id="a8a57-165">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="a8a57-166">Yığın işaretçisi, ARM işlemcisinde kayıt (R13).</span><span class="sxs-lookup"><span data-stu-id="a8a57-166">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="a8a57-167">ARM işlemcisinde veri kaydı R0.</span><span class="sxs-lookup"><span data-stu-id="a8a57-167">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="a8a57-168">ARM işlemcisinde veri kaydı R1.</span><span class="sxs-lookup"><span data-stu-id="a8a57-168">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="a8a57-169">ARM işlemcisinde veri kayıt R2.</span><span class="sxs-lookup"><span data-stu-id="a8a57-169">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="a8a57-170">ARM işlemcisinde veri kaydı R3.</span><span class="sxs-lookup"><span data-stu-id="a8a57-170">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="a8a57-171">ARM işlemcisine R4 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-171">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="a8a57-172">ARM işlemcisine R5 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-172">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="a8a57-173">ARM işlemcisine R6 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-173">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="a8a57-174">ARM işlemcisine R7 (THUMB kare işaretçisi) öğesini kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="a8a57-174">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="a8a57-175">ARM işlemcisine R8 öğesini kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="a8a57-175">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="a8a57-176">ARM işlemcisine R9 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-176">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="a8a57-177">ARM işlemcisine R10 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-177">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="a8a57-178">ARM işlemcisindeki çerçeve işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a8a57-178">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="a8a57-179">ARM işlemcisine R12 kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a8a57-179">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="a8a57-180">ARM işlemcisinde bağlantı yazmacı (R14).</span><span class="sxs-lookup"><span data-stu-id="a8a57-180">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8a57-181">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8a57-181">Remarks</span></span>  

 <span data-ttu-id="a8a57-182">IA-64 işlemcisinde 128 genel amaçlı veri kayıtları ve 128 kayan nokta veri kayıtları vardır ancak yalnızca değerler `REGISTER_IA64_R0` ve `REGISTER_IA64_F0` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a8a57-182">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="a8a57-183">Diğer değerler aşağıdaki şekilde belirlenebilir:</span><span class="sxs-lookup"><span data-stu-id="a8a57-183">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="a8a57-184">`REGISTER_IA64_R0` `REGISTER_IA64_R1` `REGISTER_IA64_R127` IA-64 işlemcisinde #127 veri kaydı aracılığıyla #1 veri kaydına karşılık gelen değerler için kayıt numarasını öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a8a57-184">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="a8a57-185">, `REGISTER_IA64_F0` `REGISTER_IA64_F1` `REGISTER_IA64_F127` IA-64 işlemcisinde #127 FP veri kaydı aracılığıyla #1 FP veri kaydına karşılık gelen değerler için kayıt numarasını öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a8a57-185">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="a8a57-186">Örneğin, IA-64 işlemcisinde #83 veri kaydını belirtmeniz gerekiyorsa `REGISTER_IA64_R0` + 83 kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8a57-186">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8a57-187">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8a57-187">Requirements</span></span>  

 <span data-ttu-id="a8a57-188">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8a57-188">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8a57-189">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a8a57-189">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8a57-190">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a8a57-190">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8a57-191">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8a57-191">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a57-192">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8a57-192">See also</span></span>

- [<span data-ttu-id="a8a57-193">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="a8a57-193">Debugging Enumerations</span></span>](debugging-enumerations.md)
