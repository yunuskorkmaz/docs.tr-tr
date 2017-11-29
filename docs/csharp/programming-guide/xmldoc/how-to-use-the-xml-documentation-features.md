---
title: "Nasıl yapılır: XML Belgeleri Özelliklerini Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb647a275a5cd5fac2316706591440d9792861b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="3e9f4-102">Nasıl yapılır: XML Belgeleri Özelliklerini Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3e9f4-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="3e9f4-103">Aşağıdaki örnek belgelenmiştir bir tür temel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e9f4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e9f4-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 <span data-ttu-id="3e9f4-105">**Bu .xml dosyası ile Yukarıdaki örnek kod oluşturuldu.**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-105">**// This .xml file was generated with the previous code sample.**</span></span>  
<span data-ttu-id="3e9f4-106">**\<? xml version = "1.0"? >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-106">**\<?xml version="1.0"?>**</span></span>  
<span data-ttu-id="3e9f4-107">**\<Belge >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-107">**\<doc>**</span></span>  
 <span data-ttu-id="3e9f4-108">**\<derleme >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-108">**\<assembly>**</span></span>  
 <span data-ttu-id="3e9f4-109">**\<adı > xmlsample \< /name >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-109">**\<name>xmlsample\</name>**</span></span>  
 <span data-ttu-id="3e9f4-110">**\</Assembly >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-110">**\</assembly>**</span></span>  
 <span data-ttu-id="3e9f4-111">**\<üyeleri >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-111">**\<members>**</span></span>  
 <span data-ttu-id="3e9f4-112">**\<üye adı "T:SomeClass" = >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-112">**\<member name="T:SomeClass">**</span></span>  
 <span data-ttu-id="3e9f4-113">**\<Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-113">**\<summary>**</span></span>  
 <span data-ttu-id="3e9f4-114">**Sınıf düzeyinde Özet belgelerine buraya ekleyin.  \< /Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-114">**Class level summary documentation goes here.\</summary>**</span></span>  
 <span data-ttu-id="3e9f4-115">**\<Açıklamalar >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-115">**\<remarks>**</span></span>  
 <span data-ttu-id="3e9f4-116">**Bir tür veya üye uzun açıklamaları ilişkilendirilebilir.**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-116">**Longer comments can be associated with a type or member**</span></span>  
 <span data-ttu-id="3e9f4-117">**Açıklamalar etiketi aracılığıyla \< /remarks >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-117">**through the remarks tag\</remarks>**</span></span>  
 <span data-ttu-id="3e9f4-118">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-118">**\</member>**</span></span>  
 <span data-ttu-id="3e9f4-119">**\<üye name="F:SomeClass.m_Name" >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-119">**\<member name="F:SomeClass.m_Name">**</span></span>  
 <span data-ttu-id="3e9f4-120">**\<Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-120">**\<summary>**</span></span>  
 <span data-ttu-id="3e9f4-121">**Name özelliği için depolama \< /Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-121">**Store for the name property\</summary>**</span></span>  
 <span data-ttu-id="3e9f4-122">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-122">**\</member>**</span></span>  
 <span data-ttu-id="3e9f4-123">**\<üye adı "M:SomeClass. #ctor" = >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-123">**\<member name="M:SomeClass.#ctor">**</span></span>  
 <span data-ttu-id="3e9f4-124">**\<Özet > sınıfı oluşturucusu.  \< /Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-124">**\<summary>The class constructor.\</summary>**</span></span>  
 <span data-ttu-id="3e9f4-125">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-125">**\</member>**</span></span>  
 <span data-ttu-id="3e9f4-126">**\<üye name="M:SomeClass.SomeMethod(System.String)" >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-126">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="3e9f4-127">**\<Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-127">**\<summary>**</span></span>  
 <span data-ttu-id="3e9f4-128">**SomeMethod açıklaması.  \< /Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-128">**Description for SomeMethod.\</summary>**</span></span>  
 <span data-ttu-id="3e9f4-129">**\<param name = "s" > s parametresi açıklamasını buraya\</param >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-129">**\<param name="s"> Parameter description for s goes here\</param>**</span></span>  
 <span data-ttu-id="3e9f4-130">**\<SeeAlso cref="T:System.String" >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-130">**\<seealso cref="T:System.String">**</span></span>  
 <span data-ttu-id="3e9f4-131">**Bir tür veya üye başvurmak için herhangi bir etiket cref özniteliği kullanabilirsiniz**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-131">**You can use the cref attribute on any tag to reference a type or member**</span></span>  
 <span data-ttu-id="3e9f4-132">**ve derleyici başvurusu var olup olmadığını denetleyin. \</seealso >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-132">**and the compiler will check that the reference exists. \</seealso>**</span></span>  
 <span data-ttu-id="3e9f4-133">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-133">**\</member>**</span></span>  
 <span data-ttu-id="3e9f4-134">**\<üye name="M:SomeClass.SomeOtherMethod" >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-134">**\<member name="M:SomeClass.SomeOtherMethod">**</span></span>  
 <span data-ttu-id="3e9f4-135">**\<Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-135">**\<summary>**</span></span>  
 <span data-ttu-id="3e9f4-136">**Diğer bir yöntem.  \< /Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-136">**Some other method. \</summary>**</span></span>  
 <span data-ttu-id="3e9f4-137">**\<döndürür >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-137">**\<returns>**</span></span>  
 <span data-ttu-id="3e9f4-138">**Dönüş sonuçları döndürür etiketi açıklanmaktadır.  \< /verir >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-138">**Return results are described through the returns tag.\</returns>**</span></span>  
 <span data-ttu-id="3e9f4-139">**\<SeeAlso cref="M:SomeClass.SomeMethod(System.String)" >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-139">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="3e9f4-140">**Belirli bir yöntemi başvurmak için cref özniteliği kullanımına dikkat edin \</seealso >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-140">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span></span>  
 <span data-ttu-id="3e9f4-141">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-141">**\</member>**</span></span>  
 <span data-ttu-id="3e9f4-142">**\<üye name="M:SomeClass.Main(System.String[])" >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-142">**\<member name="M:SomeClass.Main(System.String[])">**</span></span>  
 <span data-ttu-id="3e9f4-143">**\<Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-143">**\<summary>**</span></span>  
 <span data-ttu-id="3e9f4-144">**Uygulama için giriş noktası.**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-144">**The entry point for the application.**</span></span>  
 <span data-ttu-id="3e9f4-145">**\</ Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-145">**\</summary>**</span></span>  
 <span data-ttu-id="3e9f4-146">**\<param name = "bağımsız değişken" > bir komut satırı bağımsız değişkenleri listesi\</param >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-146">**\<param name="args"> A list of command line arguments\</param>**</span></span>  
 <span data-ttu-id="3e9f4-147">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-147">**\</member>**</span></span>  
 <span data-ttu-id="3e9f4-148">**\<üye name="P:SomeClass.Name" >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-148">**\<member name="P:SomeClass.Name">**</span></span>  
 <span data-ttu-id="3e9f4-149">**\<Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-149">**\<summary>**</span></span>  
 <span data-ttu-id="3e9f4-150">**Name özelliği  \< /Özet >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-150">**Name property \</summary>**</span></span>  
 <span data-ttu-id="3e9f4-151">**\<Değer >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-151">**\<value>**</span></span>  
 <span data-ttu-id="3e9f4-152">**Bir değer etiketi özellik değeri tanımlamak için kullanılan \< /value >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-152">**A value tag is used to describe the property value\</value>**</span></span>  
 <span data-ttu-id="3e9f4-153">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-153">**\</member>**</span></span>  
 <span data-ttu-id="3e9f4-154">**\</Members >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-154">**\</members>**</span></span>  
<span data-ttu-id="3e9f4-155">**\</ doc >**</span><span class="sxs-lookup"><span data-stu-id="3e9f4-155">**\</doc>**</span></span>   
## <a name="compiling-the-code"></a><span data-ttu-id="3e9f4-156">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3e9f4-156">Compiling the Code</span></span>  
 <span data-ttu-id="3e9f4-157">Örnek derlemek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="3e9f4-157">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="3e9f4-158">Bu TYPE komutunu kullanarak veya tarayıcınızda görüntüleyebilirsiniz XMLsample.xml XML dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-158">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3e9f4-159">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="3e9f4-159">Robust Programming</span></span>  
 <span data-ttu-id="3e9f4-160">XML belgeleri başlatır: / / / ile.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-160">XML documentation starts with ///.</span></span> <span data-ttu-id="3e9f4-161">Yeni bir proje oluşturduğunuzda, sihirbazda bazı starter / / / satırları yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-161">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="3e9f4-162">Bu açıklamalar işlenmesini bazı kısıtlamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="3e9f4-162">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="3e9f4-163">Belge doğru biçimlendirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-163">The documentation must be well-formed XML.</span></span> <span data-ttu-id="3e9f4-164">Doğru biçimlendirilmiş XML değil, bir uyarı oluşturulur ve belge dosyası bir hatayla karşılaşıldı belirten bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-164">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="3e9f4-165">Geliştiriciler kendi etiketleri kümesi oluşturmak boş.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-165">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="3e9f4-166">Önerilen etiketler (daha fazla bilgi bölümüne bakın) birtakım yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-166">There is a recommended set of tags (see the Further Reading section).</span></span> <span data-ttu-id="3e9f4-167">Önerilen etiketler bazıları özel anlamlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3e9f4-167">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="3e9f4-168">\<Param > etiketi parametrelerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-168">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="3e9f4-169">Kullandıysanız, derleyici parametresi var olduğundan ve tüm parametreleri belgelerinde açıklanan doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-169">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="3e9f4-170">Doğrulama başarısız olursa derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-170">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="3e9f4-171">`cref` Öznitelik, bir başvuru code öğesi sağlamak için herhangi bir etiket için eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-171">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="3e9f4-172">Derleyici, bu kod öğesi var olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-172">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="3e9f4-173">Doğrulama başarısız olursa derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-173">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="3e9f4-174">Derleyici herhangi uyar `using` açıklandığı bir tür için göründüğünde deyimleri `cref` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-174">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="3e9f4-175">\<Özet > etiketi IntelliSense Visual Studio içinde bir tür veya üye hakkındaki ek bilgileri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-175">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3e9f4-176">XML dosyası türü ve üyeleri hakkında tam bilgi sağlamaz (örneğin, bunu herhangi bir tür bilgi içermiyor).</span><span class="sxs-lookup"><span data-stu-id="3e9f4-176">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="3e9f4-177">Bir tür veya üye hakkında tam bilgi almak için belge dosyası gerçek tür veya üye yansıma ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-177">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9f4-178">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e9f4-178">See Also</span></span>  
 [<span data-ttu-id="3e9f4-179">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3e9f4-179">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3e9f4-180">/ doc (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="3e9f4-180">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="3e9f4-181">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="3e9f4-181">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
