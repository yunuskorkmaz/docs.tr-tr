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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82bcbf363a4fa682a85adf485596fea713457051
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409223"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="fa061-102">CorDebugRegister Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fa061-102">CorDebugRegister Enumeration</span></span>
<span data-ttu-id="fa061-103">Verilen işlemci mimarisi ile ilişkili olan kayıtları belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa061-103">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa061-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa061-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="fa061-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fa061-105">Members</span></span>  
  
|<span data-ttu-id="fa061-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fa061-106">Member</span></span>|<span data-ttu-id="fa061-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa061-107">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="fa061-108">Bir yönerge işaretçisi tüm işlemcilerde kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-108">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="fa061-109">Bir yığın işaretçisi tüm işlemcilerde kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-109">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="fa061-110">Çerçeve işaretçisi tüm işlemcilerde kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-110">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="fa061-111">Yönerge işaretçisi kasayla x86 işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-111">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="fa061-112">X86 yığın işaretçi kasayla işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-112">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="fa061-113">X86 temel işaretçi kasayla işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-113">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="fa061-114">Bir veri kaydettirmek üzerinde x86 işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-114">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="fa061-115">C verileri kaydı üzerinde x86 işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-115">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="fa061-116">D verileri kaydı üzerinde x86 işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-116">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="fa061-117">B verileri kaydı üzerinde x86 işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-117">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="fa061-118">X86 kaynak dizini kasayla işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-118">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="fa061-119">X86 hedef dizin kasayla işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-119">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="fa061-120">Yığın kasayla 0 x86 kayan nokta (FP) işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-120">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="fa061-121">#1 yığın FP işlemci üzerinde x86 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-121">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="fa061-122">#2 yığın FP işlemci üzerinde x86 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-122">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="fa061-123">#3 yığını FP işlemci üzerinde x86 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-123">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="fa061-124">#4 yığının FP işlemci üzerinde x86 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-124">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="fa061-125">#5 yığın FP işlemci üzerinde x86 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-125">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="fa061-126">#6 yığını FP işlemci üzerinde x86 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-126">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="fa061-127">#7 yığını FP işlemci üzerinde x86 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-127">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="fa061-128">Yönerge işaretçisi AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-128">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="fa061-129">Yığın işaretçisi AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-129">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="fa061-130">Temel işaretçi AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-130">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="fa061-131">Bir veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-131">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="fa061-132">C veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-132">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="fa061-133">D veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-133">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="fa061-134">B veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-134">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="fa061-135">Kaynak dizini AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-135">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="fa061-136">Hedef dizin AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-136">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="fa061-137">#8 veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-137">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="fa061-138">#9 veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-138">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="fa061-139">#10 veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-139">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="fa061-140">#11 veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-140">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="fa061-141">#12 veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-141">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="fa061-142">#13 veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-142">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="fa061-143">#14 veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-143">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="fa061-144">#15 veri AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-144">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="fa061-145">Multimedya #0 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-145">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="fa061-146">Multimedya #1 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-146">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="fa061-147">Multimedya #2 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-147">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="fa061-148">Multimedya #3 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-148">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="fa061-149">Multimedya #4 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-149">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="fa061-150">Multimedya #5 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-150">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="fa061-151">Multimedya #6 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-151">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="fa061-152">Multimedya #7 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-152">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="fa061-153">Multimedya #8 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-153">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="fa061-154">Multimedya #9 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-154">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="fa061-155">Multimedya #10 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-155">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="fa061-156">Multimedya #11 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-156">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="fa061-157">Multimedya #12 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-157">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="fa061-158">Multimedya #13 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-158">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="fa061-159">Multimedya #14 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-159">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="fa061-160">Multimedya #15 AMD64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-160">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="fa061-161">Yığın işaretçisi IA-64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-161">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="fa061-162">#0 veri IA-64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-162">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="fa061-163">#0 FP veri IA-64 işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-163">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="fa061-164">Program sayacı ARM işlemci (R15 kayıtları) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-164">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="fa061-165">Yığın işaretçisi ARM işlemci (R13) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-165">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="fa061-166">Veri R0 ARM işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-166">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="fa061-167">Veri R1 ARM işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-167">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="fa061-168">Veri R2 ARM işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-168">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="fa061-169">Veri R3 ARM işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-169">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="fa061-170">R4 ARM işlemci kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-170">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="fa061-171">ARM işlemci R5 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-171">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="fa061-172">ARM işlemci r6 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-172">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="fa061-173">R7 kaydetmek (Flash çerçeve işaretçisi) ARM işlemci.</span><span class="sxs-lookup"><span data-stu-id="fa061-173">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="fa061-174">ARM işlemci R8 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-174">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="fa061-175">ARM işlemci R9 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-175">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="fa061-176">ARM işlemci R10 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-176">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="fa061-177">ARM işlemci çerçeve işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="fa061-177">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="fa061-178">ARM işlemci R12 kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-178">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="fa061-179">Bağlantıyı ARM işlemci (R14) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fa061-179">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa061-180">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa061-180">Remarks</span></span>  
 <span data-ttu-id="fa061-181">128 genel amaçlı veri kayıtları ve IA-64 işlemci, ancak yalnızca değerleri 128 kayan nokta veri kasalarda `REGISTER_IA64_R0` ve `REGISTER_IA64_F0` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="fa061-181">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="fa061-182">Diğer değerler şu şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="fa061-182">The other values can be determined as follows:</span></span>  
  
-   <span data-ttu-id="fa061-183">Kayıt numarası eklemek `REGISTER_IA64_R0` değerleri için `REGISTER_IA64_R1` aracılığıyla `REGISTER_IA64_R127`, hangi karşılık IA-64 işlemci #127 verileri kasayla aracılığıyla #1 veri kaydı.</span><span class="sxs-lookup"><span data-stu-id="fa061-183">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
-   <span data-ttu-id="fa061-184">Kayıt numarası eklemek `REGISTER_IA64_F0` değerleri için `REGISTER_IA64_F1` aracılığıyla `REGISTER_IA64_F127`, hangi karşılık #127 aracılığıyla #1 FP veri kaydı IA-64 işlemci FP veri kaydı.</span><span class="sxs-lookup"><span data-stu-id="fa061-184">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="fa061-185">Örneğin, #83 veri kaydı IA-64 işlemci belirtmeniz gerekiyorsa, kullanın `REGISTER_IA64_R0` + 83.</span><span class="sxs-lookup"><span data-stu-id="fa061-185">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa061-186">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa061-186">Requirements</span></span>  
 <span data-ttu-id="fa061-187">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa061-187">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa061-188">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa061-188">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa061-189">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa061-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa061-190">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa061-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa061-191">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa061-191">See Also</span></span>  
 [<span data-ttu-id="fa061-192">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fa061-192">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
