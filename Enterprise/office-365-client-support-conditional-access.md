---
title: Office 365 클라이언트 응용 프로그램 지원-조건부 액세스
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
ms.collection: Strat_O365_Enterprise
description: Office 365 클라이언트 응용 프로그램 지원 조건부 액세스에 대 한 이해
ms.openlocfilehash: f9a1b4c022b00569a392d7f50bfcae583847ea3c
ms.sourcegitcommit: 4e654517825b74a3bbe171b915b134ba49231e2e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2018
ms.locfileid: "21541968"
---
# <a name="office-365-client-app-support---conditional-access"></a><span data-ttu-id="35c11-103">Office 365 클라이언트 응용 프로그램 지원-조건부 액세스</span><span class="sxs-lookup"><span data-stu-id="35c11-103">Office 365 Client App Support - Conditional Access</span></span>

<span data-ttu-id="35c11-p101">현대 직장에서 사용자 거의 모든 곳에서 다양 한 장치 및 앱을 사용 하 여 조직의 리소스에 액세스할 수 있습니다. 따라서 방금 리소스에 액세스할 수 있는 사용자에 초점을 맞추고이 충분 한 아니다. 조직에 대 한 액세스 제어 인프라에는 리소스에 액세스 하는 방법과도 지원 해야 합니다. Azure AD 장치, 위치 및 다단계 인증 기반 조건부 액세스를 사용 하 여이 새로운 요구 사항을 충족할 수 있습니다. 조건부 액세스는 하면 컨트롤에 특정 조건에 따라 모든 사용자 환경에서 앱에 대 한 액세스를 적용할 수 있도록 하는 중앙 위치에서 관리 되는 Azure Active Directory의 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="35c11-p101">In the modern workplace, users can access your organization's resources using a variety of devices and apps from virtually anywhere. As a result, just focusing on who can access a resource is not sufficient anymore. Your organization must also support how and where a resource is being accessed into your access control infrastructure. With Azure AD device, location, and multifactor authentication-based conditional access, you can meet this new requirement. Conditional access is a capability of Azure Active Directory that enables you to enforce controls on the access to apps in your environment, all based on specific conditions and managed from a central location.</span></span> 

<span data-ttu-id="35c11-109">[장치 기반](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications), [위치 기반](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations), 및 [MFA 기반](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups) 조건부 액세스 하는 방법에 대 한 자세한 내용은.</span><span class="sxs-lookup"><span data-stu-id="35c11-109">Learn more about [device-based](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications), [location-based](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations), and [MFA-based](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups) conditional access.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="35c11-110">지원되는 플랫폼</span><span class="sxs-lookup"><span data-stu-id="35c11-110">Supported platforms</span></span>

 - <span data-ttu-id="35c11-111">10 Windows 바탕 화면</span><span class="sxs-lookup"><span data-stu-id="35c11-111">Windows 10 Desktop</span></span>
 - <span data-ttu-id="35c11-112">Windows 10 현대 앱</span><span class="sxs-lookup"><span data-stu-id="35c11-112">Windows 10 Modern Apps</span></span>
 - <span data-ttu-id="35c11-113">웹 브라우저</span><span class="sxs-lookup"><span data-stu-id="35c11-113">Web Browser</span></span>
 - <span data-ttu-id="35c11-114">Android</span><span class="sxs-lookup"><span data-stu-id="35c11-114">Android</span></span>
 - <span data-ttu-id="35c11-115">iOS</span><span class="sxs-lookup"><span data-stu-id="35c11-115">iOS</span></span>
 - <span data-ttu-id="35c11-116">macOS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="35c11-116">macOS<sup>1</sup></span></span>

## <a name="supported-clients"></a><span data-ttu-id="35c11-117">지원되는 클라이언트</span><span class="sxs-lookup"><span data-stu-id="35c11-117">Supported clients</span></span>

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| <span data-ttu-id="35c11-118">![굴 아이콘](images/o365-delve-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-118">![Delve icon](images/o365-delve-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-119">Delve</span><span class="sxs-lookup"><span data-stu-id="35c11-119">Delve</span></span>](https://products.office.com/business/intelligent-search) | <span data-ttu-id="35c11-120">![Excel 아이콘](images/o365-excel-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-120">![Excel icon](images/o365-excel-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-121">Excel</span><span class="sxs-lookup"><span data-stu-id="35c11-121">Excel</span></span>](https://products.office.com/excel) | <span data-ttu-id="35c11-122">![흐름 아이콘](images/o365-flow-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-122">![Flow icon](images/o365-flow-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-123">Flow</span><span class="sxs-lookup"><span data-stu-id="35c11-123">Flow</span></span>](https://flow.microsoft.com) | <span data-ttu-id="35c11-124">![양식 아이콘](images/o365-forms-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-124">![Forms icon](images/o365-forms-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-125">Forms</span><span class="sxs-lookup"><span data-stu-id="35c11-125">Forms</span></span>](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | <span data-ttu-id="35c11-126">![Kaizala 아이콘](images/o365-kaizala-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-126">![Kaizala icon](images/o365-kaizala-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-127">Kaizala</span><span class="sxs-lookup"><span data-stu-id="35c11-127">Kaizala</span></span>](https://products.office.com/en/business/microsoft-kaizala) 
| <span data-ttu-id="35c11-128">![Office 365 관리자 아이콘](images/o365-o365admin-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-128">![Office 365 Admin icon](images/o365-o365admin-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-129">Office 365 <br> 관리</span><span class="sxs-lookup"><span data-stu-id="35c11-129">Office 365 <br> Admin</span></span>](https://products.office.com/business/manage-office-365-admin-app) | <span data-ttu-id="35c11-130">![비즈니스 아이콘 비즈니스용 OneDrive](images/o365-OneDrive-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-130">![OneDrive for Business icon](images/o365-OneDrive-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-131">OneDrive</span><span class="sxs-lookup"><span data-stu-id="35c11-131">OneDrive</span></span>](https://products.office.com/onedrive-for-business/online-cloud-storage) | <span data-ttu-id="35c11-132">![OneNote 아이콘](images/o365-OneNote-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-132">![OneNote icon](images/o365-OneNote-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-133">OneNote</span><span class="sxs-lookup"><span data-stu-id="35c11-133">OneNote</span></span>](https://products.office.com/onenote) | <span data-ttu-id="35c11-134">![Outlook 아이콘](images/o365-outlook-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-134">![Outlook icon](images/o365-outlook-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-135">Outlook</span><span class="sxs-lookup"><span data-stu-id="35c11-135">Outlook</span></span>](https://products.office.com/outlook) | <span data-ttu-id="35c11-136">![플래너 아이콘](images/o365-planner-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-136">![Planner icon](images/o365-planner-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-137">Planner</span><span class="sxs-lookup"><span data-stu-id="35c11-137">Planner</span></span>](https://products.office.com/business/task-management-software) 
| <span data-ttu-id="35c11-138">![PowerBI 아이콘](images/o365-powerbi-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-138">![PowerBI icon](images/o365-powerbi-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-139">Power BI</span><span class="sxs-lookup"><span data-stu-id="35c11-139">Power BI</span></span>](https://powerbi.microsoft.com) | <span data-ttu-id="35c11-140">![PowerPoint 아이콘](images/o365-powerpoint-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-140">![PowerPoint icon](images/o365-powerpoint-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-141">PowerPoint</span><span class="sxs-lookup"><span data-stu-id="35c11-141">PowerPoint</span></span>](https://products.office.com/powerpoint) | <span data-ttu-id="35c11-142">![프로젝트 아이콘](images/o365-project-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-142">![Project icon](images/o365-project-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-143">Project</span><span class="sxs-lookup"><span data-stu-id="35c11-143">Project</span></span>](https://products.office.com/project) | <span data-ttu-id="35c11-144">![SharePoint 아이콘](images/o365-sharepoint-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-144">![SharePoint icon](images/o365-sharepoint-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-145">Sharepoint<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="35c11-145">Sharepoint<sup>1</sup></span></span>](https://products.office.com/sharepoint) | <span data-ttu-id="35c11-146">![Skype 비즈니스 아이콘](images/o365-skypeforbusiness-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-146">![Skype for Business icon](images/o365-skypeforbusiness-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-147">용 Skype <br> 비즈니스</span><span class="sxs-lookup"><span data-stu-id="35c11-147">Skype for <br> Business</span></span>](https://www.skype.com/business/) 
| <span data-ttu-id="35c11-148">![StaffHub 아이콘](images/o365-staffhub-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-148">![StaffHub icon](images/o365-staffhub-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-149">StaffHub</span><span class="sxs-lookup"><span data-stu-id="35c11-149">StaffHub</span></span>](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | <span data-ttu-id="35c11-150">![스트림 아이콘](images/o365-stream-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-150">![Stream icon](images/o365-stream-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-151">Stream</span><span class="sxs-lookup"><span data-stu-id="35c11-151">Stream</span></span>](https://stream.microsoft.com) | <span data-ttu-id="35c11-152">![아이콘 라](images/o365-sway-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-152">![Sway icon](images/o365-sway-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-153">Sway</span><span class="sxs-lookup"><span data-stu-id="35c11-153">Sway</span></span>](https://sway.com) | <span data-ttu-id="35c11-154">![팀 아이콘](images/o365-teams-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-154">![Teams icon](images/o365-teams-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-155">Teams</span><span class="sxs-lookup"><span data-stu-id="35c11-155">Teams</span></span>](https://products.office.com/microsoft-teams/group-chat-software) | <span data-ttu-id="35c11-156">![할 일 아이콘](images/o365-todo-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-156">![To-Do icon](images/o365-todo-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-157">To-Do</span><span class="sxs-lookup"><span data-stu-id="35c11-157">To-Do</span></span>](https://todo.microsoft.com) 
| <span data-ttu-id="35c11-158">![Visio 아이콘](images/o365-visio-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-158">![Visio icon](images/o365-visio-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-159">Visio</span><span class="sxs-lookup"><span data-stu-id="35c11-159">Visio</span></span>](https://products.office.com/visio/flowchart-software) | <span data-ttu-id="35c11-160">![Word 아이콘](images/o365-word-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-160">![Word icon](images/o365-word-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-161">Word</span><span class="sxs-lookup"><span data-stu-id="35c11-161">Word</span></span>](https://products.office.com/word) | <span data-ttu-id="35c11-162">![Yammer 아이콘](images/o365-yammer-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="35c11-162">![Yammer icon](images/o365-yammer-64x64.png)</span></span> <br> [<span data-ttu-id="35c11-163">Yammer</span><span class="sxs-lookup"><span data-stu-id="35c11-163">Yammer</span></span>](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <span data-ttu-id="35c11-164"><sup>1</sup> macOS 출시 예정에 SharePoint 앱을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="35c11-164"><sup>1</sup> SharePoint app support on macOS coming soon.</span></span>